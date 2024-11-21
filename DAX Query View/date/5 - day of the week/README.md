To display the **day of the week** (e.g., "Monday", "Tuesday") along with the **date** in the format `Day-Month-YY`, you can use the `FORMAT` function in DAX with `"DD-MMMM-YY"` and `dddd` for the full day name.

### **DAX Query to View Date in `Day-Month-YY` Format**

```dax
EVALUATE
VAR CurrentDate = TODAY()
RETURN 
    ROW("FormattedDate", FORMAT(CurrentDate, "dddd-DD-MMM-YY"))
```

### **Explanation**:
- **`TODAY()`**: Returns the current date.
- **`FORMAT(CurrentDate, "dddd-DD-MMM-YY")`**: Formats the date as:
  - `dddd`: The full name of the day (e.g., "Monday").
  - `DD`: The day of the month (two digits).
  - `MMM`: The three-letter abbreviation for the month (e.g., "Nov").
  - `YY`: The last two digits of the year (e.g., "24").
- **`ROW("FormattedDate", ...)`**: Creates a one-row table with the formatted date.

### **Output Example**:
- If today's date is `2024-11-21` and it's a **Thursday**, the output will show:
  ```
  FormattedDate
  Thursday-21-Nov-24
  ```

### **Power BI (Calculated Column or Measure)**:
You can use this formula to create a **calculated column** or **measure** in **Power BI**:

#### **Calculated Column**:
```dax
FormattedDate = FORMAT(TODAY(), "dddd-DD-MMM-YY")
```

#### **Measure**:
```dax
FormattedDate = FORMAT(TODAY(), "dddd-DD-MMM-YY")
```

This will display the day name along with the date in the `Day-Month-YY` format (e.g., `Thursday-21-Nov-24`) in your Power BI visuals.

Let me know if you need further modifications!