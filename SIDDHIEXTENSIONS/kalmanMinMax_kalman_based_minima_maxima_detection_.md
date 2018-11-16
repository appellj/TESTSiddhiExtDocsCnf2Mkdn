# kalmanMinMax (kalman based minima maxima detection)

The `kalmanMinMax` function uses the `kalman` filter to smooth the time
series values in the given window size, and then determine the maxima
and minima of that set of values.

### Input parameters 

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required/Optional</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Variable</td>
<td>Required</td>
<td>The time series value to be considered for minima maxima detection.</td>
</tr>
<tr class="even">
<td>Q</td>
<td>Required</td>
<td>The standard deviation of the process noise.</td>
</tr>
<tr class="odd">
<td><p>R</p></td>
<td>Required</td>
<td>The standard deviation of the measurement noise.</td>
</tr>
<tr class="even">
<td><p>Window Size</p></td>
<td>Required</td>
<td>The number of values to be considered for smoothing and determining the extremes.</td>
</tr>
<tr class="odd">
<td>Extrema Type</td>
<td>Required</td>
<td>This can be <code>min</code>, <code>max</code> or <code>minmax</code>.</td>
</tr>
</tbody>
</table>

### Output parameters

| Parameter        | Name                                                | Description                                                             |
|------------------|-----------------------------------------------------|-------------------------------------------------------------------------|
| min or max value | The variable name specified in the input parameter. | The value of the `min` or `max` point.                                  |
| extrema Type     | extrema Type                                        | Indicates whether the returned value is a `min` value or a `max` value. |

### Examples

##### Minimum values

The following returns the maximum values for a set of `price `values.

``` sql
from inputStream#timeseries:kalmanMinMax(price, 0.000001,0.0001, 25, 'min')
select *
insert into outputStream;
```

 

##### Maximum values

The following returns the minimum values for a set of `price` values.

``` sql
from inputStream#timeseries:kalmanMinMax(price, 0.000001,0.0001, 25, max)
select *
insert into outputStream;
```

##### Minimum and maximum values

The following returns both the minimum values and the maximum values
for a set of `price` values.

``` sql
from inputStream#timeseries:kalmanMinMax(price, 0.000001,0.0001, 25, 'minmax')
select *
insert into outputStream;
```
