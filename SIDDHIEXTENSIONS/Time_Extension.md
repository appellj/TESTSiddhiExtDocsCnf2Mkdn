# Time Extension

This extension provides time related functionality to Siddhi such as
getting the current time, current date, manipulating/formatting dates,
etc. Following are the functions of the time extension.

-   [Current Date function](#TimeExtension-CurrentDatefunction)
-   [Current Time function](#TimeExtension-CurrentTimefunction)
-   [Current Timestamp
    function](#TimeExtension-CurrentTimestampfunction)
-   [Date Adding function](#TimeExtension-DateAddingfunction)
-   [Date Subtraction function](#TimeExtension-DateSubtractionfunction)
-   [Date Difference function](#TimeExtension-DateDifferencefunction)
-   [Date Format function](#TimeExtension-DateFormatfunction)
-   [Extract function](#TimeExtension-Extractfunction)
-   [Date function](#TimeExtension-Datefunction)
-   [Timestamp In Milliseconds
    function](#TimeExtension-TimestampInMillisecondsfunction)
-   [UTC Timestamp function](#TimeExtension-UTCTimestampfunction)

### Current Date function

|                |                                                             |
|----------------|-------------------------------------------------------------|
| Syntax         | `<string> time:currentDate ( )`                             |
| Extension Type | Function                                                    |
| Description    | Returns the current system date in the `yyyy-MM-dd` format. |
| Example        | `currentDate()` returns `2015-08-20`.                       |

 

### Current Time function

|                |                                                           |
|----------------|-----------------------------------------------------------|
| Syntax         | `<string> currentTime ( )`                                |
| Extension Type | Function                                                  |
| Description    | Returns the current system time in the `HH:mm:ss` format. |
| Example        | `currentTime()` returns `13:15:10`.                       |

 

### Current Timestamp function

|                |                                                                           |
|----------------|---------------------------------------------------------------------------|
| Syntax         | `<string> time:           currentTimestamp ( )`                           |
| Extension Type | Function                                                                  |
| Description    | Returns the current system timestamp in the `yyyy-MM-dd HH:mm:ss` format. |
| Example        | `currentTimestamp()` returns `2015-08-20 13:15:10`.                       |

**  
**

### **Date Adding function**

The common parameters of this function are described below.

-   **`dateValue`** : A value of date.
    e.g., `"2014-11-11 13:23:44.657"`, `"2014-11-11"`, `"13:23:44.657"`
-   **`expr`** : The amount by which the selected part of the date
    format should be incremented. e.g., 2 ,5 ,10 etc.
-   **`unit`** : The part of the date format that needs to be
    manipulated.
    e.g., `"MINUTE"` , `"HOUR"` , `"MONTH"` , `"YEAR"` , `"QUARTER"` ,
    \*` "WEEK"` , `"DAY"` , `"SECOND"`
-   **`dateFormat`** : The date format of the date value provided.
    e.g., `yyyy-MM-dd HH:mm:ss.SSS     `
-   **`timestampInMilliseconds`** : The date value in milliseconds (from
    the epoch). e.g.,` 1415712224000L`

|                |                                                                                                                                                                                        |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> time:           dateAdd (<string> dateValue , <long> expr, <string> unit, <string> dateFormat )`                                                                             |
| Extension Type | Function                                                                                                                                                                               |
| Description    | Returns the specified date and time with the selected `           unit          `of the specified `           dateValue         ` incremented by the given amount (i.e.  **`expr`** ). |
| Example        | `dateAdd("2014-11-11 13:23:44", 2, 'year',"yyyy-MM-dd HH:mm:ss")` returns `"2016-11-11 13:23:44"`.                                                                                     |

|                |                                                                                                                                                                                             |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> time:           dateAdd (<string>  dateValue  , < long >  expr,  <string>  unit )`                                                                                                |
| Extension Type | Function                                                                                                                                                                                    |
| Description    | Returns the specified date and time with the selected `           unit         ` ** **of the specified `           dateValue         ` incremented by the given amount (i.e.  **`expr`** ). |
| Example        | `dateAdd("2014-11-11 13:23:44", 2, 'year')` returns `"2016-11-11 13:23:44"`.                                                                                                                |

|                |                                                                                                                                                                                                        |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> time:           dateAdd (<long>  timestampInMilliseconds, < long >   expr,  <string>  unit )`                                                                                                |
| Extension Type | Function                                                                                                                                                                                               |
| Description    | Returns the specified time stamp with the selected `           unit         ` ** **of the specified `           timestampInMilliseconds         ` incremented by the given amount (i.e.  **`expr`** ). |
| Example        | `dateAdd(1415692424000L, 2, 'year')` returns `"2016-11-11 13:23:44"`.                                                                                                                                  |

**  
**

### **Date Subtraction function**

The common parameters of this function are described below.

-   **`dateValue`** : A value of date.
    e.g., `"2014-11-11 13:23:44.657"`, `"2014-11-11"`, `"13:23:44.657"`
-   **`expr`** : The amount by which the selected part of the date
    format should be reduced. e.g., 2 ,5 ,10 etc.
-   **`unit`** : The part of the date format that needs to be
    manipulated.
    e.g., `"MINUTE"` , `"HOUR"` , `"MONTH"` , `"YEAR"` , `"QUARTER"` ,
    \*` "WEEK"` , `"DAY"` , `"SECOND"`
-   **`dateFormat`** : The date format of the date value provided.
    e.g., `yyyy-MM-dd HH:mm:ss.SSS     `
-   **`timestampInMilliseconds`** : The date value in milliseconds (from
    the epoch). e.g.,` 1415712224000L`

|                |                                                                                                                                                                                    |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> time:           dateSub (<string> dateValue , <long> expr, <string> unit, <string> dateFormat )`                                                                         |
| Extension Type | Function                                                                                                                                                                           |
| Description    | Returns the specified date and time with the selected `           unit          `of the specified `           dateValue         ` reduced by the given amount (i.e.  **`expr`** ). |
| Example        | `dateSub("2014-11-11 13:23:44", 2, 'year',"yyyy-MM-dd HH:mm:ss")` returns `"2012-11-11 13:23:44"`.                                                                                 |

|                |                                                                                                                                                                                              |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> time:           dateSub (<string>  dateValue  , < long >  expr,  <string>  unit )`                                                                                                 |
| Extension Type | Function                                                                                                                                                                                     |
| Description    | Returns the specified date and time stamp with he selected `           unit         ` ** **of the specified `           dateValue         ` reduced by the given amount (i.e.  **`expr`** ). |
| Example        | `dateSub("2014-11-11 13:23:44", 2, 'year')` returns `"2012-11-11 13:23:44".`                                                                                                                 |

|                |                                                                                                                                                                                                     |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> time:           dateSub (<long>  timestampInMilliseconds,  < long >   expr,  <string>  unit )`                                                                                            |
| Extension Type | Function                                                                                                                                                                                            |
| Description    | Returns the specified time stamp with the selected `           unit         ` ** **of the specified `           timestampInMilliseconds         `  reduced by the given amount (i.e.  **`expr`** ). |
| Example        | ` dateSub(1415692424000L, 2, 'year')` returns `1352620424000.`                                                                                                                                      |

**  
**

### **Date Difference function**

The common parameters of this function are described below.

-   **`dateValue1`** : A value of date.
    e.g., `"2014-11-11 13:23:44.657"`, `"2014-11-11"` , `"13:23:44.657"`
-   **`dateValue2`** : A value of date.
    e.g., `"2014-11-11 13:23:44.657"`, `"2014-11-11"` , `"13:23:44.657"`
-   **`dateFormat1`** : The date format of  **`dateValue1`** .
    e.g., `yyyy-MM-dd HH:mm:ss.SSS     `
-   **`dateFormat2`** : The date format of  **`dateValue2`** .
    e.g., `yyyy-MM-dd HH:mm:ss.SSS     `
-   **`timestampInMilliseconds1`** : A date value in milliseconds (from
    the epoch) e.g., `1415712224000L`
-   **`timestampInMilliseconds2`** :A date value in milliseconds (from
    the epoch) e.g., `1415712224000L`

|                |                                                                                                                                 |
|----------------|---------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<int> time:           dateDiff (<string> dateValue1 ,  < string >  dateValue2 ,  <string> dateFormat1, <string> dateFormat2 )` |
| Extension Type | Function                                                                                                                        |
| Description    | Returns the number of days between the two dates specified (i.e.  **`dateValue1`**  and  **`dateValue2`** ).                    |
| Example        | `dateDiff('2014-11-11 13:23:44', '2014-11-9 13:23:44', 'yyyy-MM-dd HH:mm:ss', 'yyyy-MM-dd HH:mm:ss')` returns `2`.              |

|                |                                                                                                              |
|----------------|--------------------------------------------------------------------------------------------------------------|
| Syntax         | `<int> time:           dateDiff (<string> dateValue1 ,  < string >  dateValue2 )`                            |
| Extension Type | Function                                                                                                     |
| Description    | Returns the number of days between the two dates specified (i.e.  **`dateValue1`**  and  **`dateValue2`** ). |
| Example        | `dateDiff('2014-11-11 13:23:44.000', '2014-11-9 13:23:44.000'`) returns `2`.                                 |

|                |                                                                                                                                                                                     |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<int> time:           dateDiff (<string> timestampInMilliseconds1 ,  < string >  timestampInMilliseconds2 )`                                                                       |
| Extension Type | Function                                                                                                                                                                            |
| Description    | Returns the number of days between the two date and time stamps specified (i.e. `           timestampInMilliseconds1         ` and `           timestampInMilliseconds2         `). |
| Example        | `dateDiff(1415692424000, 1415519624000)` returns `2`.                                                                                                                               |

 

### Date Format function

The common parameters of this function are described below.

-   **`dateValue`** : -A value of date.
    e.g.,` "2014-11-11 13:23:44.657`", `"2014-11-11"` , `"13:23:44.657" `
-   **`dateTargetFormat`** : The date format to which the specified 
    **`date value`**  needs to be converted. e.g., `yyyy/MM/dd HH:mm:ss`
-   **`dateSourceFormat`** : The date format of the  **`date value`**
     provided. e.g., `yyyy-MM-dd HH:mm:ss.SSS     `
-   **`timestampInMilliseconds`** : A date value in milliseconds (from
    the epoch) e.g., `1415712224000L`

|                |                                                                                                                  |
|----------------|------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> time:           dateFormat(<string>  dateValue,<string>  dateTargetFormat,<string>  dateSourceFormat)` |
| Extension Type | Function                                                                                                         |
| Description    | Returns a formatted date string.                                                                                 |
| Example        | `dateFormat('2014-11-11 13:23:55', 'ss', 'yyyy-MM-dd HH:mm:ss')` returns `55`.                                   |

|                |                                                                                       |
|----------------|---------------------------------------------------------------------------------------|
| Syntax         | `<string> time:           dateFormat(<string>  dateValue,<string>  dateTargetFormat)` |
| Extension Type | Function                                                                              |
| Description    | Returns a formatted date string.                                                      |
| Example        | `dateFormat('2014-11-11 13:23:55.657', 'ss')` returns `55`.                           |

|                |                                                                                                     |
|----------------|-----------------------------------------------------------------------------------------------------|
| Syntax         | `<string>  time:           dateFormat (<long> timestampInMilliseconds ,<string>  dateTargetFormat)` |
| Extension Type | Function                                                                                            |
| Description    | Returns a formatted date string.                                                                    |
| Example        | `dateFormat(1415692424000, 'yyyy-MM-dd')` returns `2014-11-11.`                                     |

 

### Extract function

-   **`dateValue`** : A value of date.
    e.g., `"2014-11-11 13:23:44.657"`, `"2014-11-11"` , `"13:23:44.657" `
-   **`unit`** : The part of the date format that needs to be
    manipulated.
    e.g., `"MINUTE"` , `"HOUR"` , `"MONTH"` , `"YEAR"` , `"QUARTER"` ,
    \*` "WEEK"` , `"DAY"` , `"SECOND"`
-   **`dateFormat`** : The date format of the date value provided.
    e.g., `yyyy-MM-dd HH:mm:ss.SSS     `
-   **`timestampInMilliseconds`** : A date value in milliseconds (from
    the epoch) e.g., `1415712224000L`

|                |                                                                                                  |
|----------------|--------------------------------------------------------------------------------------------------|
| Syntax         | `<int>  time:           extract (<string> unit ,<string>  dateValue, <string> dataFormat)`       |
| Extension Type | Function                                                                                         |
| Description    | Returns the specified `           unit         ` extracted from the specified  **`dateValue`** . |
| Example        | `extract('year', '2014-3-11 02:23:44', 'yyyy-MM-dd hh:mm:ss')` returns `2014`.                   |

|                |                                                                                                  |
|----------------|--------------------------------------------------------------------------------------------------|
| Syntax         | `<int>  time:           extract (<string> unit ,<string>  dateValue)`                            |
| Extension Type | Function                                                                                         |
| Description    | Returns the specified `           unit         ` extracted from the specified  **`dateValue`** . |
| Example        | `extract('year', '2014-3-11 02:23:44.234')` returns `2014`.                                      |

|                |                                                                                                                              |
|----------------|------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<int>  time:           extract (<long> timestampInMilliseconds ,<string>  unit)`                                            |
| Extension Type | Function                                                                                                                     |
| Description    | Returns the specified `           unit         ` extracted from the specified `           timestampInMilliseconds         `. |
| Example        | `extract(1394484824000, 'year')` returns `2014`.                                                                             |

 

### Date function

|                |                                                                             |
|----------------|-----------------------------------------------------------------------------|
| Syntax         | `<string>  time:           date (<string> dateValue ,<string>  dateFormat)` |
| Extension Type | Function                                                                    |
| Description    | Returns the date component of the `dateValue`.                              |
| Example        | `date('2014-11-11 13:23:44', 'yyyy-MM-dd HH:mm:ss')` returns `2014-11-11`.  |

 

### Timestamp In Milliseconds function

|                |                                                      |
|----------------|------------------------------------------------------|
| Syntax         | `<long>  time:           timestampInMilliseconds ()` |
| Extension Type | Function                                             |
| Description    | Returns the current time stamp in milliseconds.      |
| Example        | `timestampInMilliseconds()` returns `1440160328693`. |

|                |                                                                                                                                                                                                            |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<long>  time:           timestampInMilliseconds (<string> dateValue)`                                                                                                                                     |
| Extension Type | Function                                                                                                                                                                                                   |
| Description    | Returns the time stamp of the specified  **`dateValue`**  in milliseconds. In order to use this function, the date format of the specified  **`dateValue`**  should be `yyyy-MM-dd HH:mm:ss.SSS         `. |
| Example        | `timestampInMilliseconds('2007-11-30 10:30:19.000')` returns `1196398819000`.                                                                                                                              |

|                |                                                                                                                                                  |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<long>  time:           timestampInMilliseconds (<string> dateValue, <string> dateFormat)`                                                      |
| Extension Type | Function                                                                                                                                         |
| Description    | Returns the time stamp of the specified  **`dateValue`**  in milliseconds. The date format can be specified in the  **`dateForma`** t parameter. |
| Example        | `timestampInMilliseconds('2007-11-30 10:30:19', 'yyyy-MM-dd HH:mm:ss')` returns `1196398819000`.                                                 |

### ** UTC Timestamp function**

|                |                                                                   |
|----------------|-------------------------------------------------------------------|
| Syntax         | `<string> time:           utcTimestamp()`                         |
| Extension Type | Function                                                          |
| Description    | Returns the system time in the` yyyy-MM-dd HH:mm:ss` date format. |
| Example        | `utcTimestamp()` returns `2015-08-21 12:16:13`.                   |
