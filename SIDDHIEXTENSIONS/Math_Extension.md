# Math Extension

Math extension provides basic mathematical functions such as calculating
absolute value, sin, cos, tan, base conversion, parsing, etc. Following
are the functions of the Math extension. 

-   [Absolute Value function](#MathExtension-AbsoluteValuefunction)
-   [acos  function](#MathExtension-acosfunction)
-   [asin function](#MathExtension-asinfunction)
-   [atan function](#MathExtension-atanfunction)
-   [Binary function](#MathExtension-Binaryfunction)
-   [Ceiling function](#MathExtension-Ceilingfunction)
-   [Convert function](#MathExtension-Convertfunction)
-   [CopySign function](#MathExtension-CopySignfunction)
-   [cos function](#MathExtension-cosfunction)
-   [cosh function](#MathExtension-coshfunction)
-   [Cube Root function](#MathExtension-CubeRootfunction)
-   [e function](#MathExtension-efunction)
-   [Exponential function](#MathExtension-Exponentialfunction)
-   [Floor function](#MathExtension-Floorfunction)
-   [Get Exponent function](#MathExtension-GetExponentfunction)
-   [Hexadecimal function](#MathExtension-Hexadecimalfunction)
-   [Is Infinite function](#MathExtension-IsInfinitefunction)
-   [Is Not A Number function ](#MathExtension-IsNotANumberfunction)
-   [ln function](#MathExtension-lnfunction)
-   [log2 function](#MathExtension-log2function)
-   [log10 function](#MathExtension-log10function)
-   [log function](#MathExtension-logfunction)
-   [Max function](#MathExtension-Maxfunction)
-   [Min function](#MathExtension-Minfunction)
-   [Octal function](#MathExtension-Octalfunction)
-   [Parse Double function](#MathExtension-ParseDoublefunction)
-   [Parse Float function](#MathExtension-ParseFloatfunction)
-   [Parse Int function](#MathExtension-ParseIntfunction)
-   [Parse Long function](#MathExtension-ParseLongfunction)
-   [Percentile function](#MathExtension-Percentilefunction)
-   [pi function](#MathExtension-pifunction)
-   [Power function](#MathExtension-Powerfunction)
-   [Random function](#MathExtension-Randomfunction)
-   [Round function](#MathExtension-Roundfunction)
-   [Sign of Number function](#MathExtension-SignofNumberfunction)
-   [sin function](#MathExtension-sinfunction)
-   [sinh function](#MathExtension-sinhfunction)
-   [Square Root function](#MathExtension-SquareRootfunction)
-   [tan  function](#MathExtension-tanfunction)
-   [tanh function](#MathExtension-tanhfunction)
-   [To Degrees function](#MathExtension-ToDegreesfunction)
-   [To Radians function](#MathExtension-ToRadiansfunction)

### **Absolute Value function**

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;double&gt; math:abs(&lt;float|double&gt; p1)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns the absolute value of  <strong><code>p1</code></strong> . This function wraps the <code>java.lang.Math.abs()</code> function.</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><p>Both the following queries return 3 since the absolute value of both <code>3</code> and <code>-3</code> is <code>3</code>.</p>
<ul>
<li><code>abs(3)</code></li>
<li><code>abs(-3)</code></li>
</ul></td>
</tr>
</tbody>
</table>

**  
**

### **acos**  function

|                |                                                                                                                                                                                                                     |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           acos(<float|double> p1)`                                                                                                                                                                  |
| Extension Type | Function                                                                                                                                                                                                            |
| Description    | If **-1 &lt;= p1 &lt;= 1**, this function returns the arc-cosine (inverse cosine) of `p1`. If not, it returns `NULL.` The return value is in radian scale. This function wraps the `java.lang.Math.acos()`function. |
| Example        | `acos(0.5)` returns `1.0471975511965979`.                                                                                                                                                                           |

 

### asin function

|                |                                                                                                                                                                                                                       |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           asin (<float|double>  p1)`                                                                                                                                                                  |
| Extension Type | Function                                                                                                                                                                                                              |
| Description    | If **-1 &lt;= p1 &lt;= 1**, this function returns the arc-sin (inverse sine) of  **`p1`** . If not, it returns `NULL`. The return value is in radian scale. This function wraps the `java.lang.Math.asin()` function. |
| Example        | `asin(0.5)` returns `0.5235987755982989`.                                                                                                                                                                             |

 

### atan function

|                |                                                                                                                                                   |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           atan(<int|long|float|double> p1)`                                                                                       |
| Extension Type | Function                                                                                                                                          |
| Description    | Returns the arc-tangent (inverse tangent) of `p1`. The return value is in radian scale. This function wraps the `java.lang.Math.atan()` function. |
| Examples       | `atan(6d)` returns `1.4056476493802699`.                                                                                                          |

|                |                                                                                                                                                                                                                  |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           atan (<int|long|float|double> p1, <int|long|float|double> p2)`                                                                                                                         |
| Extension Type | Function                                                                                                                                                                                                         |
| Description    | Returns the arc-tangent (inverse tangent) of  `           p1         ` and `           p2         ` coordinates. The return value is in radian scale. This function wraps the` java.lang.Math.atan2()` function. |
| Examples       | `atan(12d, 5d)` returns `1.1760052070951352`.                                                                                                                                                                    |

 

### Binary function

|                |                                                                                                                                                                                                                |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string>  math:           bin(<int|long> p1)         `                                                                                                                                                        |
| Extension Type | Function                                                                                                                                                                                                       |
| Description    | Returns a string representation of the integer/long **p1** argument as an unsigned integer in base `2`. This function wraps the `java.lang.Integer.toBinaryString` and`java.lang.Long.toBinaryString` methods. |
| Examples       | ` bin(9)` returns `"1001"`.                                                                                                                                                                                    |

 

### Ceiling function

|                |                                                                                                                                                                                                                       |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           ceil(<float|double> p1)`                                                                                                                                                                   |
| Extension Type | Function                                                                                                                                                                                                              |
| Description    | Returns the smallest (closest to negative infinity) double value that is greater than or equal to the **p1** argument, and is equal to a mathematical integer. This function wraps the`java.lang.Math.ceil()` method. |
| Example        | `ceil(423.187d)` returns `424.0`.                                                                                                                                                                                     |

 

### Convert function

|                |                                                                               |
|----------------|-------------------------------------------------------------------------------|
| Syntax         | `<string>  math:           conv(<string> a, <int> fromBase, <int> toBase)`    |
| Extension Type | Function                                                                      |
| Description    | Converts  **`a`**  from the  **`fromBase`**  base to the  **`toBase`**  base. |
| Example        | `conv("7f", 16, 10)` returns `"127"`.                                         |

 

### CopySign function

|                |                                                                                                                                          |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           copySign(<int|long|float|double> magnitude, <int|long|float|double> sign)`                                    |
| Extension Type | Function                                                                                                                                 |
| Description    | Returns the magnitude of  **`magnitude`**  with the sign of  **`sign`**  . This function wraps the `java.lang.Math.copySign()` function. |
| Example        | `copySign(5.6d, -3.0d)` returns `-5.6`.                                                                                                  |

 

### cos function

|                |                                                                                                                       |
|----------------|-----------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           cos(<int|long|float|double> p1)`                                                           |
| Extension Type | Function                                                                                                              |
| Description    | Returns the cosine of  **`p1`**  ( **`p1`**  is in radians). This function wraps the `java.lang.Math.cos()` function. |
| Example        | `cos(6d)` returns `0.9601702866503661`.                                                                               |

 

### cosh function

|                |                                                                                                                                   |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           cosh(<int|long|float|double> p1)`                                                                      |
| Extension Type | Function                                                                                                                          |
| Description    | Returns the hyperbolic cosine of  **`p1`**  ( **`p1`**  is in radians). This function wraps the `java.lang.Math.cosh()` function. |
| Example        | `cosh (6d) `returns `201.7156361224559`.                                                                                          |

 

### Cube Root function

|                |                                                                                                                           |
|----------------|---------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           cbrt(<int|long|float|double> p1)`                                                              |
| Extension Type | Function                                                                                                                  |
| Description    | Returns the cube-root of  **`p1`**  ( **`p1`**  is in radians). This function wraps the `java.lang.Math.cbrt()` function. |
| Example        | `cbrt(17d) `returns `2.5712815906582356`.                                                                                 |

 

### e function

|                |                                                                                                                                        |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           e()`                                                                                                        |
| Extension Type | Function                                                                                                                               |
| Description    | Returns the `java.lang.Math.E` constant, which is the closest double value to  **`e`**  (which is the base of the natural logarithms). |
| Example        | `e()` returns `2.7182818284590452354`.                                                                                                 |

 

### Exponential function

|                |                                                                                                                                    |
|----------------|------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           exp(<int|long|float|double> p1)`                                                                        |
| Extension Type | Function                                                                                                                           |
| Description    | Returns Euler's number  **`e`**  raised to the power of  **`p1`** . This function wraps the  **`java.lang.Math.exp()`**  function. |
| Example        | `exp(10.23)` returns `27722.51006805505`.                                                                                          |

### Floor function

|                |                                                                                                                                                                                                           |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           floor(<int|long|float|double> p1)`                                                                                                                                             |
| Extension Type | Function                                                                                                                                                                                                  |
| Description    | This function wraps the `java.lang.Math.floor()` function that returns the largest (closest to positive infinity) value that is less that or equal to  **`p1`** , and is equal to a mathematical integer. |
| Example        | `floor(10.23)` returns `10.0.`                                                                                                                                                                            |

 

### Get Exponent function

|                |                                                                                                                                          |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double>  math:           getExponent(<int|long|float|double>  p1)`                                                                     |
| Extension Type | Function                                                                                                                                 |
| Description    | Returns the unbiased exponent used in the representation of  **`p1`** . This function wraps the `java.lang.Math.getExponent()` function. |
| Example        | `getExponent(60984.1)` returns `15`.                                                                                                     |

 

### Hexadecimal function

|                |                                                                                                                                   |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string>  math:           hex(<int|long|float|double> p1)`                                                                       |
| Extension Type | Function                                                                                                                          |
| Description    | This function wraps the `java.lang.Double.toHexString()` function that returns a hexadecimal string representation of  **`p1`** . |
| Example        | `hex(200)` returns `"c8"`.                                                                                                        |

 

### Is Infinite function

|                |                                                                                                                                                                                                           |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<boolean>  math:           isInfinite(<float|double>  p1)`                                                                                                                                               |
| Extension Type | Function                                                                                                                                                                                                  |
| Description    | This function wraps the `java.lang.Float.isInfinite()` and `java.lang.Double.isInfinite() `functions that return `true` if  **`p1`**  is infinitely large in magnitude, or return  **`false`** otherwise. |
| Example        | `isInfinite(java.lang.Double.POSITIVE_INFINITY)` returns `true`.                                                                                                                                          |

 

### Is Not A Number function 

|                |                                                                                                                                                                                         |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `< boolean>  math:           isNan(<float|double>  p1)`                                                                                                                                 |
| Extension Type | Function                                                                                                                                                                                |
| Description    | This function wraps the `java.lang.Float.isNaN()` and `java.lang.Double.isNaN() `functions that return `true` if  **`p1`**  is a `NaN` (Not-a-Number) value, or return false otherwise. |
| Example        | `isNan(java.lang.Math.log(-12d)`) returns` true`.                                                                                                                                       |

 

### ln function

|                |                                                              |
|----------------|--------------------------------------------------------------|
| Syntax         | `<double> math:           ln (< int|long|float|double > p1)` |
| Extension Type | Function                                                     |
| Description    | Returns the natural logarithm (base e) of  **`p1`** .        |
| Example        | `ln(11.453)` returns `2.438251704415579`.                    |

 

### log2 function

|                |                                                                 |
|----------------|-----------------------------------------------------------------|
| Syntax         | `<double> math:           log2 (< int|long|float|double >  p1)` |
| Extension Type | Function                                                        |
| Description    | Returns the `base 2` logarithm of  **`p1`** .                   |
| Example        | `log2(91d)` returns `6.507794640198696`.                        |

 

### log10 function

|                |                                                                    |
|----------------|--------------------------------------------------------------------|
| Syntax         | `<double> math:           log10 ( < int|long|float|double >  p1 )` |
| Extension Type | Function                                                           |
| Description    | Returns the base 10 logarithm of **p1**.                           |
| Example        | `log10(19.234)` returns` 1.2840696117100832`.                      |

 

### log function

|                |                                                                                                      |
|----------------|------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           log (< int|long|float|double >  number, < int|long|float|double >  base )` |
| Extension Type | Function                                                                                             |
| Description    | Returns the logarithm (base=base) of  **`number`** .                                                 |
| Example        | `log(34, 2f)` returns `5.08746284125034`.                                                            |

 

### Max function

|                |                                                                                                |
|----------------|------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           max (< int|long|float|double >  p1,  <int|long|float|double>   p2 )` |
| Extension Type | Function                                                                                       |
| Description    | Returns the greater value out of  **`p1`**  and  **`p2`** .                                    |
| Example        | `max(123.67d, 91) `returns `123.67`.                                                           |

 

### Min function

|                |                                                                                                |
|----------------|------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           min (< int|long|float|double >  p1,  <int|long|float|double>   p2 )` |
| Extension Type | Function                                                                                       |
| Description    | Returns the smaller value out of  **`p1`**  and  **`p2`** .                                    |
| Example        | `min(123.67d, 91)` returns `91`.                                                               |

 

### Octal function

|                |                                                 |
|----------------|-------------------------------------------------|
| Syntax         | `<string> math:           oct (<int|long>  p1)` |
| Extension Type | Function                                        |
| Description    | Converts  **`p1`**  to octal.                   |
| Example        | `oct(99l)` returns `"143"`.                     |

 

### Parse Double function

|                |                                                        |
|----------------|--------------------------------------------------------|
| Syntax         | `<double> math:           parseDouble (<string>  str)` |
| Extension Type | Function                                               |
| Description    | Returns `str` as a double.                             |
| Example        | `parseDouble("123")` returns `123.0`.                  |

 

### Parse Float function

|                |                                                      |
|----------------|------------------------------------------------------|
| Syntax         | `<float> math:           parseFloat (<string>  str)` |
| Extension Type | Function                                             |
| Description    | Returns `str `as a float.                            |
| Example        | `parseFloat("123")` returns `123.0`.                 |

 

### Parse Int function

|                |                                                  |
|----------------|--------------------------------------------------|
| Syntax         | `<int> math:           parseInt (<string>  str)` |
| Extension Type | Function                                         |
| Description    | Returns `str` as an int.                         |
| Example        | `parseInt("123")` returns `123`.                 |

 

### Parse Long function

|                |                                                    |
|----------------|----------------------------------------------------|
| Syntax         | `<long> math:           parseLong (<string>  str)` |
| Extension Type | Function                                           |
| Description    | Returns `str` as a long.                           |
| Example        | `parseLong("123")` returns `123`.                  |

 

### Percentile function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td> math: <strong>percentile </strong> (  arg ,    <strong>p</strong> )</td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns the pth percentile value of the arg values. </td>
</tr>
<tr class="even">
<td>Example</td>
<td><p>from inputStream#window.length(100)</p>
<p>select math:percentile(temperature, 97.0) as percentile</p>
<p>insert into outputStream;</p>
<p>returns 97th percentile value of last 100 <code>temperature</code> values. </p></td>
</tr>
</tbody>
</table>

 

### pi function

|                |                                                                                                                                                  |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           pi ( )`                                                                                                                |
| Extension Type | Function                                                                                                                                         |
| Description    | Returns the `java.lang.Math.PI` constant, which is the closest value to `pi` (i.e. the ratio of the circumference of a circle to its diameter).  |
| Example        | `pi()` always returns `3.141592653589793`.                                                                                                       |

 

### Power function

|                |                                                                                                          |
|----------------|----------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           power ( < int|long|float|double>  value,  <int|long|float|double>   toPower )` |
| Extension Type | Function                                                                                                 |
| Description    | Returns `value` raised to the power of `toPower`.                                                        |
| Example        | `power(5.6d, 3.0d)` returns `175.61599999999996`.                                                        |

 

### Random function

|                |                                                                                                                                           |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           rand ( )`                                                                                                       |
| Extension Type | Function                                                                                                                                  |
| Description    |  A sequence of calls to `rand()` generates a stream of pseudo-random numbers. This function uses the `java.util.Random` class internally. |
| Example        | Two sequential calls to `rand()` may return `0.8263929447650588` and `0.24425883860361197` respectively.                                  |

|                |                                                                                                                                               |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           rand (< int|long >  seed)`                                                                                          |
| Extension Type | Function                                                                                                                                      |
| Description    | A sequence of calls to `rand(seed`) generates a stream of pseudo-random numbers. This function uses the `java.util.Random` class internally.  |
| Example        | Two sequential calls to `rand(12)` may return `0.7298928061101974` and `0.2750691655200749`, respectively.                                    |

 

### Round function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>&lt;int&gt; math:             round (&lt;float&gt; value )</code></p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Funcion</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns the closest integer value to the argument.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>round(3.35)</code> returns <code>3</code>.</td>
</tr>
</tbody>
</table>

|                |                                                  |
|----------------|--------------------------------------------------|
| Syntax         | `<long> math:           round (<double> value )` |
| Extension Type | Function                                         |
| Description    | Returns the closest long value to the argument.  |
| Example        | `round(3252.353)` returns `3252`.                |

 

### Sign of Number function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;int&gt; math:           signum (&lt; int|long|float|double &gt;  p1)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><ul>
<li>If <code>a</code> is a positive, this returns the sign of  <strong><code>p1</code></strong>  as <code>1.0</code>.</li>
<li>If <code>a</code> is a negative, this returns the sign of  <strong><code>p1</code></strong>  as -<code>1.0</code>.</li>
<li>If <code>a</code> is neither a positive or a negative, this returns the sign of  <strong><code>p1</code></strong>  as <code>0.0</code>.</li>
</ul>
<p>This function wraps the <code>java.lang.Math.signum()</code> function.</p></td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>signum(-6.32d)</code> returns <code>-1</code>.</td>
</tr>
</tbody>
</table>

 

### sin function

|                |                                                                                                                     |
|----------------|---------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           sin (< int|long|float|double >  p1)`                                                      |
| Extension Type | Function                                                                                                            |
| Description    | Returns the sine of  **`p1`**  ( **`p1`**  is in radians). This function wraps the `java.lang.Math.sin()` function. |
| Example        | `sin(6d`) returns `-0.27941549819892586.`                                                                           |

 

### sinh function

|                |                                                                                                                                  |
|----------------|----------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           sinh (< int|long|float|double >  p1)`                                                                  |
| Extension Type | Function                                                                                                                         |
| Description    | Returns the hyperbolic sine of  **`p1`**  ( **`p1`**  is in radians). This function wraps the `java.lang.Math.sinh()` function.  |
| Example        | `sinh(6d)` returns `201.71315737027922`.                                                                                         |

 

### Square Root function

|                |                                                                                                   |
|----------------|---------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           sqrt (< int|long|float|double >  p1)`                                   |
| Extension Type | Function                                                                                          |
| Description    | Returns the square-root of  **`p1`** . This function wraps the` java.lang.Math.sqrt()` function.  |
| Example        | `sqrt(4d)` returns `2`.                                                                           |

 

### tan  function

|                |                                                                                                                     |
|----------------|---------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           tan (< int|long|float|double >  p1)`                                                      |
| Extension Type | Function                                                                                                            |
| Description    | Returns the tan of  **`p1`**  ( **`p1`**  is in radians). This function wraps the `java.lang.Math.tan()` function.  |
| Example        | `tan(6d)` returns `-0.29100619138474915`.                                                                           |

 

### tanh function

|                |                                                                                                                                     |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           tanh (<int|long|float|double>  p1)`                                                                       |
| Extension Type | Function                                                                                                                            |
| Description    | Returns the hyperbolic tangent of  **`p1`**  ( **`p1`**  is in radians). This function wraps the `java.lang.Math.tanh()` function.  |
| Example        | `tanh(6d)` returns `0.9999877116507956`.                                                                                            |

 

### To Degrees function

|                |                                                                                                                           |
|----------------|---------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           toDegrees (< int|long|float|double >  p1)`                                                      |
| Extension Type | Function                                                                                                                  |
| Description    | Converts `           p1         ` from radians to degrees. This function wraps the `java.lang.Math.toDegrees()` function. |
| Example        | `toDegrees(6d)` returns `343.77467707849394`.                                                                             |

 

### To Radians function

|                |                                                                                                             |
|----------------|-------------------------------------------------------------------------------------------------------------|
| Syntax         | `<double> math:           toRadians (< int|long|float|double >  p1)`                                        |
| Extension Type | Function                                                                                                    |
| Description    | Converts  **`p1`**  from degrees to radians. This function wraps the `java.lang.Math.toRadians()` function. |
| Example        | `toRadians(6d)` returns `0.10471975511965977`.                                                              |
