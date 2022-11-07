# SQL Basic Replication

### Basic SQL Query used for replication

-----------------
 
```SQL
MERGE [DESTINATION].[dbo].[TABLE] AS D
USING [SOURCE].[dbo].[TABLE] AS S WITH (NOLOCK) 

ON (D.[COLUMN1] = S.[COLUMN1] and D.[COLUMN2] = S.[COLUMN2] and D.[COLUMN3] = S.[COLUMN3])

---- 3. Update Target with Source
WHEN MATCHED THEN
UPDATE set D.[COLUMN1] = S.[COLUMN1],D.[COLUMN2] = S.[COLUMN2],D.[COLUMN3] = S.[COLUMN3],D.[COLUMN4] = S.[COLUMN4],D.[COLUMN5] = S.[COLUMN5]

---- 4. Insert Unmatched into Target
WHEN NOT MATCHED By TARGET THEN
INSERT ([COLUMN1],[COLUMN2],[COLUMN3],[COLUMN4],[COLUMN5])
Values ([COLUMN1],[COLUMN2],[COLUMN3],[COLUMN4],[COLUMN5]);
    ```