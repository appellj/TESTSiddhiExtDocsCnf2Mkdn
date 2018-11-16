# Outlier

Siddhi allows you to identify outliers using linear regression on real
time data streams. The `outlier` function takes in a dependent event
stream (Y), an independent event stream (X) and a user specified range
for outliers, and returns an output to indicate whether the current
event is an outlier based on the regression equation that fits
historical data.

The two implementations of `outlier` function can be distinguished as
follows.

-   **outlier**: This allows you to specify a batch size (optional) that
    defines the number of events to be considered for the calculation of
    regression when finding outliers.
-   **lengthTimeO**utlier**** : This allows you to restrict the number
    of events considered for the regression calculation performed when
    finding outliers based on a specified time window and/or a batch
    size.

Input parameters of each implementation are as follows.

### **Input parameters for the outlier function**

The following table describes the input parameters available for the
`outlier` function.

| Parameter            | Description                                                                 | Required/Optional | Default Value               |
|----------------------|-----------------------------------------------------------------------------|-------------------|-----------------------------|
| Calculation Interval | The frequency with which the regression calculations should be carried out. | Optional          | `1` (i.e., for every event) |
| Batch Size           | The maximum number of events to be used for a regression calculation.       | Optional          | `100,000,000`               |
| Confidence Interval  | The confidence interval to be used for a regression calculation.            | Optional          | `0.95`                      |
| Range                | The number of standard deviations from the regression equation.             | Required          | `0.95`                      |
| Y Stream             | The data stream of the dependent variable.                                  | Required          |                             |
| X Stream             | The data stream of the independent variable.                                | Required          |                             |

**Format**: outlier(range, Y, X) or outlier(calculation interval, batch
size, confidence interval, range, Y, X) 

### **Input Parameters for Length Time Outlier Function**

The following table describes the input parameters available for the
`lengthTimeOutlier` function.

| Parameter            | Description                                                                | Required/Option | Default Value         |
|----------------------|----------------------------------------------------------------------------|-----------------|-----------------------|
| Time Window          | The maximum time duration to be considered for a regression calculation.   | Required        |                       |
| Batch Size           | The maximum number of events to be used for a regression calculation.      | Required        |                       |
| Range                | The number of standard deviations from the regression calculation.         | Required        |                       |
| Calculation Interval | The frequency with which the regression calculation should be carried out. | Optional        | `1 `(for every event) |
| Confidence Level     | The confidence interval to be used for a regression calculation.           | Optional        | `0.95`                |
| Y Stream             | The data stream of the dependent variable.                                 | Required        |                       |
| X Stream             | The data stream of the independent variable.                               | Required        |                       |

**Format**: `lengthTimeOutlier(time window, batch size, range, Y, X)` or
`lengthTimeOutlier(time window, batch size, range, calculation interval, confidence interval, Y, X)`

### **Output parameters** ****

The following table describes the output parameters.

The same output parameters are available for each implementation.

| Parameter         | Name                                | Description                                        |
|-------------------|-------------------------------------|----------------------------------------------------|
| Outlier           | `outlier`                           | `True` if the event is an outlier, `False` if not. |
| Standard Error    | `stdError`                          | The standard error of the regression equation.     |
| β coefficients    | `beta0`, `beta1`                    | β coefficients of the regression equation.         |
| Input Stream Data | The name given in the input stream. | All the items sent in the input stream.            |

### Examples

In each example given below, the query returns an indication whether the
current event is an outlier or not together with the standard error of
the regression equation (ε), β coefficients and all the items available
in the input stream.

#### Example 1

The following query submits the number of standard deviations to be used
as a range (2), a dependent input stream (Y) and an independent input
stream (X) that are used to perform linear regression between Y and X.
It returns an output that indicates whether the current event is an
outlier or not.

``` sql
from StockExchangeStream#timeseries:outlier(2, Y, X)
select *
insert into StockForecaster 
```

#### Example 2

The following query submits a time window (2 seconds), a batch size (100
events), the number of standard deviations to be used as a range (2), a
dependent input stream (Y) and an independent input stream (X), that are
used to perform linear regression between Y and X. It returns an output
that indicates whether the current event is an outlier or not.

``` sql
from StockExchangeStream#timeseries:lengthTimeOutlier(2 sec, 100, 2, Y, X)
select *
insert into StockForecaster  
```
