# India Election Analysis 

Right — there’s no **Alliance** column in your CSV, so we’ll have to **create it first** in Power BI as a **calculated column** before we can make the seat count and percentage measures.

Here’s exactly what you’d do in **Power BI** with your `constituencywise_results` table (since it already contains one row per winning candidate, it’s cleaner than `constituencywise_details`).

---

## **1️⃣ Create Alliance Column**

Go to **Modeling → New Column** and paste this:

```DAX
Party Alliance = 
IF(
    partywise_results[Party] = "Bharatiya Janata Party - BJP" ||
    partywise_results[Party] = "Telugu Desam - TDP" ||
    partywise_results[Party] = "Janata Dal  (United) - JD(U)" ||
    partywise_results[Party] = "Shiv Sena - SHS" ||
    partywise_results[Party] = "AJSU Party - AJSUP" ||
   partywise_results[Party] = "Apna Dal (Soneylal) - ADAL" ||
    partywise_results[Party] = "Asom Gana Parishad - AGP" ||
    partywise_results[Party] = "Hindustani Awam Morcha (Secular) - HAMS" ||
    partywise_results[Party] = "Janasena Party - JnP" ||
    partywise_results[Party] = "Janata Dal  (Secular) - JD(S)" ||
    partywise_results[Party] = "Lok Janshakti Party(Ram Vilas) - LJPRV" ||
    partywise_results[Party] = "Nationalist Congress Party - NCP" ||
    partywise_results[Party]= "Rashtriya Lok Dal - RLD" ||
    partywise_results[Party] = "Sikkim Krantikari Morcha - SKM",
    "NDA",
    IF(
        partywise_results[Party] = "Indian National Congress - INC" ||
        partywise_results[Party] = "Aam Aadmi Party - AAAP" ||
        partywise_results[Party] = "All India Trinamool Congress - AITC" ||
        partywise_results[Party] = "Bharat Adivasi Party - BHRTADVSIP" ||
        partywise_results[Party]= "Communist Party of India  (Marxist) - CPI(M)" ||
        partywise_results[Party] = "Communist Party of India  (Marxist-Leninist)  (Liberation) - CPI(ML)(L)" ||
        partywise_results[Party] = "Communist Party of India - CPI" ||
        partywise_results[Party] = "Dravida Munnetra Kazhagam - DMK" ||
        partywise_results[Party] = "Indian Union Muslim League - IUML" ||
        partywise_results[Party] = "Jammu & Kashmir National Conference - JKN" ||
        partywise_results[Party] = "Jharkhand Mukti Morcha - JMM" ||
        partywise_results[Party] = "Kerala Congress - KEC" ||
        partywise_results[Party] = "Marumalarchi Dravida Munnetra Kazhagam - MDMK" ||
        partywise_results[Party] = "Nationalist Congress Party Sharadchandra Pawar - NCPSP" ||
        partywise_results[Party] = "Rashtriya Janata Dal - RJD" ||
        partywise_results[Party] = "Rashtriya Loktantrik Party - RLTP" ||
        partywise_results[Party] = "Revolutionary Socialist Party - RSP" ||
        partywise_results[Party] = "Samajwadi Party - SP" ||
        partywise_results[Party] = "Shiv Sena (Uddhav Balasaheb Thackrey) - SHSUBT" ||
        partywise_results[Party] = "Viduthalai Chiruthaigal Katchi - VCK",
        "I.N.D.I.A.",
        "OTHER"
    )
)
```

---

## **2️⃣ Create Measures**

**Total Seats**

```DAX
Total Seats =
COUNTROWS('constituencywise_results')
```

```
Total Seats = SUM(partywise_results[Won])
```

```
EVALUATE
    ROW("Total Seats", SUM(partywise_results[Won]))
```

**NDA Seats**

```DAX
NDA Seats = CALCULATE([Total Seats], partywise_results[Party Alliance] = "NDA")
```

**I.N.D.I.A Seats**

```DAX
INDIA Seats = CALCULATE([Total Seats], partywise_results[Party Alliance] = "I.N.D.I.A")
```

**NDA Percentage**

```DAX
NDA % =
DIVIDE([NDA Seats], [Total Seats], 0)
```

**I.N.D.I.A Percentage**

```DAX
INDIA % =
DIVIDE([INDIA Seats], [Total Seats], 0)
```

---

If we use this method with `constituencywise_results`,
✅ We **don’t need to filter max votes** per constituency.
✅ It works directly with winners.

Do you want me to **add all your CSV’s NDA/I.N.D.I.A party names** into that DAX list so it exactly matches your data? That way you can paste it and get 100% correct results.
