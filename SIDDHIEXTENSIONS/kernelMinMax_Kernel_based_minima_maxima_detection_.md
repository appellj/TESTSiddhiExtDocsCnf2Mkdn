# kernelMinMax (Kernel based minima maxima detection)

The `kernalMinMax` function uses Gaussian Kernel to smooth the time
series values in the given window size, and then determine the maxima
and minima of that set of values.

### Input parameters

| Parameter    | Required/Optional | Description                                                                       |
|--------------|-------------------|-----------------------------------------------------------------------------------|
| Variable     | Required          | The time series value to be considered for minima maxima detection.               |
| bandwidth    | Required          | The bandwidth of the Gaussian Kernel calculation.                                 |
| window size  | Required          | The number of values to be considered for smoothing and determining the extremes. |
| Extrema type | Required          | This can be `min`, `max` or `minmax.`                                             |

### Output parameters

| Parameter        | Name                                                | Description                                                             |
|------------------|-----------------------------------------------------|-------------------------------------------------------------------------|
| min or max value | The variable name specified in the input parameter. | The value of the `min` or `max` point.                                  |
| extremaType      | extrema Type                                        | Indicates whether the returned value is a `min` value or a `max` value. |

### Examples

##### Minimum values

The following returns the maximum values for a set of `price` values.

``` sql
from inputStream#timeseries:kernelMinMax(price, 3, 7, ‘min’)
select *
insert into outputStream;
```

 

##### Maximum values

The following returns the minimum values for a set of `price` values.

``` sql
from inputStream#timeseries:kernelMinMax(price, 3, 7, 'max')
select *
insert into outputStream;
```

 

##### Minimum and maximum values

The following returns both the minimum values and the maximum values
for a set of `price` values.

``` sql
from inputStream#timeseries:kernelMinMax(price, 3, 7, ‘minmax’)
select *
insert into outputStream;
```
