Reference: 
* https://stackoverflow.com/questions/8901161/convert-a-sql-server-datetime-to-a-shorter-date-format 
* https://stackoverflow.com/questions/22623971/first-day-of-the-next-month  

**Convert Datetime to Date:** 
```sql
cast(getdate() as date )
```
**How to get the next month day 1 based on current datetime?**
``` sql 
DATEADD(d, 1, EOMONTH(current_timestamp))  # sql server 2012+ 
DATEADD(m, DATEDIFF(m, -1, current_timestamp), 0)   # sql 2008 and older 
# example: get next 2 month's first day: 
select DATEADD(d, 1, EOMONTH(DATEADD(d, 1, EOMONTH(current_timestamp)))) 
```
**Using T-sql to remove part of string before or after specific characters; 
to get the substring between some specific strings** 
``` sql 

SELECT LEFT(string_expression, CHARINDEX(expression_to_find, string_expression) - 1)

SELECT REPLACE(SUBSTRING(string_expression, 
CHARINDEX(expression_to_find, string_expression), LEN(string_expression)), string_pattern, string_replacement)

# my demo query: parse contnets started with "assessment / plan"
select 
b.*, 
REPLACE(SUBSTRING([NoteContents], 
CHARINDEX('ASSESSMENT / PLAN', [NoteContents]),
LEN([NoteContents])), 'ASSESSMENT / PLAN', '') AS Notes
```

more detialed can be found here:
* https://basitaalishan.com/2014/02/23/removing-part-of-string-before-and-after-specific-character-using-transact-sql-string-functions/ 
* https://stackoverflow.com/questions/18362260/a-sql-query-to-select-a-string-between-two-known-strings 

How to insert the auto current date when a new row is added into the table? 
https://www.itsupportguides.com/knowledge-base/sql-server/sql-server-how-to-set-a-datetime-field-to-automatically-use-current-datetime/ 
basically you can change the default value from the design mode from SSMS. 

the way of escaping single quote in sql-server: 
https://stackoverflow.com/questions/1586560/how-do-i-escape-a-single-quote-in-sql-server 
you use '' to escape single '

How to deal with pivot rows and columns? 
https://stackoverflow.com/questions/29569801/dynamic-pivot-needed-with-row-number 

how to use cte 
https://stackoverflow.com/questions/18941275/joining-multiple-common-table-expressions 

how to get max value rows from multiple similar rows: 
https://stackoverflow.com/questions/612231/how-can-i-select-rows-with-maxcolumn-value-distinct-by-another-column-in-sql 

how to get rid of the last n characters from the string in T-sql? 
SELECT LEFT(YourColumnName, LEN(YourColumnName) - 1) FROM YourTable   
