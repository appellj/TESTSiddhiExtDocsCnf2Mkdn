# Forecast

Siddhi allows you to forecast future events using linear regression on
real time data streams. The `forecast` function uses a dependent event
stream (Y), an independent event stream (X) and a user-specified next X
value, and returns the forecast Y value based on the regression equation
of the historical data.

The two implementations of the `forecast` function can be distinguished
as follows.

-   **forecast**: This allows you to specify a batch size (optional)
    that defines the number of events to be considered for the
    regression calculation when forecasting the Y value.
-   **lengthTimeForecast**: This allows you to restrict the number of
    events considered for the regression calculation when forecasting
    the Y value based on a specified time window and/or batch size.

### **Input parameters for the forecast function**

The following table describes the input parameters available for the
`forecast` function.

| Parameter            | Description                                                                                        | Required/Optional | Default Value               |
|----------------------|----------------------------------------------------------------------------------------------------|-------------------|-----------------------------|
| Calculation Interval | The frequency with which the regression calculation should be carried out.                         | Optional          | `1` (i.e., for every event) |
| Batch Size           | The maximum number of events that should be used for a regression calculation.                     | Optional          | `1,000,000,000`             |
| Confidence Interval  | The confidence interval to be used for a regression calculation.                                   | Optional          | `0.95`                      |
| Next X Value         | The value to be used to forecast the Y value. This can be a constant or an expression (e.g., x+5). | Required          |                             |
| Y Stream             | The data stream of the dependent variable.                                                         | Required          |                             |
| X Stream             | The data stream of the independent variable.                                                       | Required          |                             |

**Format**: `forecast(nextX, Y, X)` or
`forecast(calculation interval, batch size, confidence interval, nextX, Y, X)`

### **Input parameters for the lengthTimeForecast function**

The following table describes the input parameters available for the
`lengthTimeForecast` function.

| Parameter            | Description                                                                                        | Required/Optional | Default Value               |
|----------------------|----------------------------------------------------------------------------------------------------|-------------------|-----------------------------|
| Time Window          | The maximum time duration that should be considered for a regression calculation.                  | Required          |                             |
| Batch Size           | The maximum number of events that shoukd be used for a regression calculation.                     | Required          |                             |
| Next X Value         | The value to be used to forecast the Y value. This can be a constant or an expression (e.g., x+5). | Required          |                             |
| Calculation Interval | The frequency with which the regression calculation should be carried out.                         | Optional          | `1` (i.e., for every event) |
| Confidence Interval  | The confidence interval to be used for a regression calculation.                                   | Optional          | `0.95`                      |
| Y Stream             | The data stream of the dependent variable.                                                         | Required          |                             |
| X Stream             | The data stream of the independent variable.                                                       | Required          |                             |

**Format**: `lengthTimeForecast(time window, batch size, nextX, Y, X)`
or
`lengthTimeForecast(time window, batch size, nextX, calculation interval, confidence interval, Y, X)`

### **Output parameters**

The following table describes the output parameters.

The same output parameters are available for each implementation.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Parameter</strong></p></th>
<th><p><strong>Name</strong></p></th>
<th><p><strong>Description</strong></p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Forecast Y</p></td>
<td><p><code>forecastY</code></p></td>
<td><p>The forecast Y value based on next X and regression equation.</p></td>
</tr>
<tr class="even">
<td><p>Standard Error</p></td>
<td><p><code>stdError</code></p></td>
<td><p>The standard error of the regression equation.</p></td>
</tr>
<tr class="odd">
<td><p>β coefficients</p></td>
<td><p><code>beta0</code>, <code>beta1</code></p></td>
<td><p>β coefficients of the simple linear regression.</p></td>
</tr>
<tr class="even">
<td><p>Input Stream Data</p></td>
<td><p>The name given in the input stream.</p></td>
<td><p>All the items sent in the input stream.</p></td>
</tr>
</tbody>
</table>

### Examples

The queries given in the examples below return the following wen
executed.

-   Y value based on the regression equation established using the Y
    stream and the X stream
-   The standard error of the regression equation (ε)
-   β coefficients
-   All the items available in the input stream

#### **Example 1**

The following query submits an expression to be used as the next X value
(X+2), a dependent input stream (Y,) and an independent input stream (X)
that are used to perform linear regression between Y and X streams, and
compute the forecast Y value based on the next X value specified by you.

``` sql
from StockExchangeStream#timeseries:forecast(X+5, Y, X)
select *
insert into StockForecaster
```

#### **Example 2**

The following query submits a time window (2 seconds), a batch size (100
events), a constant to be used as the next X value (10), a dependent
input stream (Y) and an independent input stream (X) that are used to
perform linear regression between Y and X streams, and compute the
forecast Y value based on the next X value specified by you.

``` sql
from StockExchangeStream#timeseries:lengthTimeForecast(2 sec, 100, 10, Y, X)
select *
insert into StockForecaster
```
