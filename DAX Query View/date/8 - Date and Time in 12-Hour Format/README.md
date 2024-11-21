To display the time in a **12-hour format** along with the **AM/PM** designation, you can adjust the DAX `FORMAT` function to use `"hh:mm:ss AM/PM"`.

### **DAX Query to View Date and Time in 12-Hour Format**

```dax
EVALUATE
VAR CurrentDateTime = NOW()
RETURN 
    ROW("FormattedDateTime", FORMAT(CurrentDateTime, "ddd-DD-MMM-YY hh:mm:ss AM/PM"))
```

### **Explanation**:
- **`NOW()`**: Returns the current date and time.
- **`FORMAT(CurrentDateTime, "ddd-DD-MMM-YY hh:mm:ss AM/PM")`**: Formats the date and time as:
  - `ddd`: The abbreviated day of the week (e.g., "Mon").
  - `DD`: The day of the month (two digits).
  - `MMM`: The three-letter abbreviation for the month (e.g., "Nov").
  - `YY`: The last two digits of the year (e.g., "24").
  - `hh`: Hours in 12-hour format.
  - `mm`: Minutes (two digits).
  - `ss`: Seconds (two digits).
  - `AM/PM`: Displays the AM/PM designation.
- **`ROW("FormattedDateTime", ...)`**: Creates a one-row table with the formatted date and time.

### **Output Example**:
- If today's date is `2024-11-21` and the time is `3:45:12 PM`, the output will show:
  ```
  FormattedDateTime
  Thu-21-Nov-24 03:45:12 PM
  ```

### **Power BI (Calculated Column or Measure)**:
In **Power BI**, you can create either a **calculated column** or **measure** to display the current date and time in the 12-hour format with AM/PM.

#### **Calculated Column**:
```dax
FormattedDateTime = FORMAT(NOW(), "ddd-DD-MMM-YY hh:mm:ss AM/PM")
```

#### **Measure**:
```dax
FormattedDateTime = FORMAT(NOW(), "ddd-DD-MMM-YY hh:mm:ss AM/PM")
```

This will show the date and time in the format `Day-Month-YY hh:mm:ss AM/PM` (e.g., `Thu-21-Nov-24 03:45:12 PM`).

Let me know if you need any more modifications!