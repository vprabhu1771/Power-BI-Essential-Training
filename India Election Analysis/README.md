# India Election Analysis 

Right — there’s no **Alliance** column in your CSV, so we’ll have to **create it first** in Power BI as a **calculated column** before we can make the seat count and percentage measures.

Here’s exactly what you’d do in **Power BI** with your `constituencywise_results` table (since it already contains one row per winning candidate, it’s cleaner than `constituencywise_details`).

---

## **1️⃣ Create Alliance Column**

Go to **Modeling → New Column** and paste this:

```DAX
Alliance =
SWITCH(
    TRUE(),
    'constituencywise_results'[Party] IN {
        "Bharatiya Janata Party",
        "Shiv Sena - SHS",
        "Janata Dal (United) - JD(U)",
        "Lok Janshakti Party (Ram Vilas) - LJPRV",
        "Ajsu Party - AJSUP",
        "Apna Dal (Soneylal) - ADAL",
        "Nationalist Congress Party - NCP",
        "Rashtriya Lok Janshakti Party - RLJP",
        "United People's Party, Liberal - UPPL",
        "Asom Gana Parishad - AGP",
        "Sikkim Krantikari Morcha - SKM"
    }, "NDA",
    'constituencywise_results'[Party] IN {
        "Indian National Congress",
        "Dravida Munnetra Kazhagam - DMK",
        "Aam Aadmi Party - AAAP",
        "All India Trinamool Congress - AITC",
        "Communist Party of India  (Marxist) - CPI(M)",
        "Communist Party of India - CPI",
        "Samajwadi Party - SP",
        "Shiv Sena (Uddhav Balasaheb Thackrey) - SHSUBT",
        "Rashtriya Janata Dal - RJD",
        "Nationalist Congress Party – Sharadchandra Pawar - NCPSP",
        "Jammu & Kashmir National Conference - JKN",
        "Jharkhand Mukti Morcha - JMM",
        "Rashtriya Lok Dal - RLD"
    }, "I.N.D.I.A",
    "Other"
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
EVALUATE
    ROW("Total Seats", SUM(partywise_results[Won]))
```

**NDA Seats**

```DAX
NDA Seats =
CALCULATE(
    COUNTROWS('constituencywise_results'),
    'constituencywise_results'[Alliance] = "NDA"
)
```

**I.N.D.I.A Seats**

```DAX
INDIA Seats =
CALCULATE(
    COUNTROWS('constituencywise_results'),
    'constituencywise_results'[Alliance] = "I.N.D.I.A"
)
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
