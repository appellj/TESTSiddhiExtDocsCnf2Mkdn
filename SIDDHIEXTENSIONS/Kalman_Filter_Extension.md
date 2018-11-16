# Kalman Filter Extension

This extension provides Kalman filtering capabilities to Siddhi. This
allows you to detect outliers of input data. Following are the functions
of the Kalman Filter extension.

-   [Kalman Filter
    function](#KalmanFilterExtension-KalmanFilterfunction)

### **Kalman Filter function**

This function uses measurements observed over time containing noise and
other inaccuracies, and produces estimated values for the current
measurement using Kalman algorithms. The parameters used are as follows.

-   **`measuredValue`**: The sequential change in the observed
    measurement. e.g., 40.695881
-   `measuredChangingRate`: The rate at which the measured change is
    taking place. e.g., The velocity with which the measured value is
    changed can be 0.003 meters per second.
-   `measurementNoiseSD`: The standard deviation of the noise. e.g.,
    0.01
-   **`timestamp`**: The time stamp of the time at which the measurement
    was carried out.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;double, double&gt; kf:kalmanFilter(&lt;double&gt; measuredValue)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Example</td>
<td><ul>
<li>1st round: <code>kf:kalmanFilter(-74.178444)</code> returns an estimated value of <code>-74.178444</code>.</li>
<li>2nd round: <code>kf:kalmanFilter(-74.175703)</code> returns an estimated value of <code>-74.1770735006853</code>.</li>
<li>3rd round: <code>kf:kalmanFilter(-74.177872)</code> returns an estimated value of  <code>-74.1773396670348</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;double, double&gt; kf:kalmanFilter(&lt;double&gt; measuredValue, &lt;double&gt; measurementNoiseSD)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Example</td>
<td><ul>
<li>1st round: <code>kf:kalmanFilter(-74.178444, 0.003)</code> returns an estimated value of <code>-74.178444</code>.</li>
<li>2nd round: <code>kf:kalmanFilter(-74.175703, 0.003)</code> returns an estimated value of <code>-74.17707350205573</code>.</li>
<li>3rd round: <code>kf:kalmanFilter(-74.177872, 0.003)</code> returns an estimated value of  <code>-74.177339667771</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;double, double&gt; kf:kalmanFilter(&lt;double&gt; measuredValue,  &lt;double&gt; measuredChangingRate, &lt;double&gt; measurementNoiseSD, &lt;long&gt; timestamp)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Example</td>
<td><ul>
<li>1st round: <code>kf:kalmanFilter(-74.178444, 0.003, 0.01, time:timestampInMilliseconds() )</code> returns an estimated value of <code>-74.1784439700006</code>.</li>
<li>2nd round: <code>kf:kalmanFilter(-74.178444, 0.003, 0.01, time:timestampInMilliseconds() )</code> returns an estimated value of <code>-74.1784439700006</code>.</li>
<li>3rd round: <code>kf:kalmanFilter(-74.177872, 0.003, 0.01, time:timestampInMilliseconds())</code> returns an estimated value of  <code>-74.17697314316393</code>.</li>
</ul></td>
</tr>
</tbody>
</table>
