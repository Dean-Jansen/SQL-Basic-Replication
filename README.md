# SQL Basic Replication

### Basic SQL Query used for replication

-----------------
 
```SQL
MERGE [DESTINATION].[dbo].[TABLE] AS T
USING [SOURCE].[dbo].[TABLE] AS S WITH (NOLOCK) 

ON (T.[COLUMN1] = S.[COLUMN1] and T.[COLUMN2] = S.[COLUMN2] and T.[COLUMN3] = S.[COLUMN3])

---- 3. Update Target with Source
WHEN MATCHED THEN
UPDATE set T.[COLUMN1] = S.[COLUMN1],T.[COLUMN2] = S.[COLUMN2],T.[COLUMN3] = S.[COLUMN3],T.[COLUMN4] = S.[COLUMN4],T.[COLUMN5] = S.[COLUMN5]

---- 4. Insert Unmatched into Target
WHEN NOT MATCHED By TARGET THEN
INSERT ([COLUMN1],[COLUMN2],[COLUMN3],[COLUMN4],[COLUMN5])
Values ([COLUMN1],[COLUMN2],[COLUMN3],[COLUMN4],[COLUMN5]);
    ```