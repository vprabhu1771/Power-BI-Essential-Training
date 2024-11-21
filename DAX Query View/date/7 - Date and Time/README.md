To display the **current time** along with the **date** in Power BI using DAX, you can use the `NOW()` function. The `NOW()` function returns the current date and time. You can format it to show the time along with the date in the desired format (e.g., `Day-Month-YY HH:MM:SS`).

### **DAX Query to View Date and Time in `Day-Month-YY HH:MM:SS` Format**

```dax
EVALUATE
VAR CurrentDateTime = NOW()
RETURN 
    ROW("FormattedDateTime", FORMAT(CurrentDateTime, "ddd-DD-MMM-YY HH:mm:ss"))
```

### **Explanation**:
- **`NOW()`**: Returns the current date and time.
- **`FORMAT(CurrentDateTime, "ddd-DD-MMM-YY HH:mm:ss")`**: Formats the date and time as:
  - `ddd`: The abbreviated day of the week (e.g., "Mon").
  - `DD`: The day of the month (two digits).
  - `MMM`: The three-letter abbreviation for the month (e.g., "Nov").
  - `YY`: The last two digits of the year (e.g., "24").
  - `HH`: Hours in 24-hour format.
  - `mm`: Minutes (two digits).
  - `ss`: Seconds (two digits).
- **`ROW("FormattedDateTime", ...)`**: Creates a one-row table with the formatted date and time.

### **Output Example**:
- If today's date is `2024-11-21` and the time is `15:45:12`, the output will show:
  ```
  FormattedDateTime
  Thu-21-Nov-24 15:45:12
  ```

### **Power BI (Calculated Column or Measure)**:
You can use the same formula to create either a **calculated column** or **measure** for date and time in Power BI.

#### **Calculated Column**:
```dax
FormattedDateTime = FORMAT(NOW(), "ddd-DD-MMM-YY HH:mm:ss")
```

#### **Measure**:
```dax
FormattedDateTime = FORMAT(NOW(), "ddd-DD-MMM-YY HH:mm:ss")
```

This will display the current time along with the date in the format `Day-Month-YY HH:MM:SS` (e.g., `Thu-21-Nov-24 15:45:12`).

Let me know if you need further assistance or adjustments!