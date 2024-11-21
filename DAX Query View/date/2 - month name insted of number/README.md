To display the **month name** (e.g., "November" instead of `11`) in the `DD-Month-YYYY` format, you can use the `FORMAT` function in DAX with `"DD-MMMM-YYYY"` format.

### **DAX Query to View Date in `DD-Month-YYYY` Format**

```dax
EVALUATE
VAR CurrentDate = TODAY()
RETURN 
    ROW("FormattedDate", FORMAT(CurrentDate, "DD-MMMM-YYYY"))
```

### **Explanation**:
- **`TODAY()`**: Returns the current date.
- **`FORMAT(CurrentDate, "DD-MMMM-YYYY")`**: Formats the current date as `DD-MMMM-YYYY`, where `MMMM` is the full month name.
- **`ROW("FormattedDate", ...)`**: Creates a one-row table with a column named `FormattedDate` containing the formatted date.

### **Output Example**:
- If today's date is `2024-11-21`, the output will show:
  ```
  FormattedDate
  21-November-2024
  ```

### **Power BI (Calculated Column or Measure)**:
If you want to apply this in **Power BI** for a calculated column or measure:

#### **Calculated Column**:
```dax
FormattedDate = FORMAT(TODAY(), "DD-MMMM-YYYY")
```

#### **Measure**:
```dax
FormattedDate = FORMAT(TODAY(), "DD-MMMM-YYYY")
```

These formulas will display the date as `DD-Month-YYYY` (e.g., `21-November-2024`) in your Power BI report. 

Let me know if you'd like further customization!