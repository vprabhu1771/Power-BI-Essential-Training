

EVALUATE
VAR CurrentDate = TODAY()
RETURN 
    ROW("FormattedDate", FORMAT(CurrentDate, "DD-MM-YYYY"))