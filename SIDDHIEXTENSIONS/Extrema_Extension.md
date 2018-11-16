# Extrema Extension

-   [bottomKLengthBatch](#bottomKLengthBatch)
-   [topKLength Batch](#topKLengthBatch)
-   [bottomK](#bottomK)
-   [topK](#topK)
-   [bottomKTimeBatch](#bottomKTimeBatch)
-   [topKTimeBatch](#topKTimeBatch)
-   [maxByLengthBatch](#maxByLengthBatch)
-   [minByLengthBatch](#minByLengthBatch)
-   [maxByLength](#maxByLength)
-   [minByLength](#minByLength)
-   [maxByTimeBatch](#maxByTimeBatch)
-   [minByTimeBatch](#minByTimeBatch)
-   [maxByTime](#maxByTime)
-   [minByTime](#minByTime)
-   [kalmanMinMax](#kalmanMinMax)
-   [kernalMinMax](#kernalMinMax)
-   [minMax](#minMax)

### bottomKLengthBatch

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>extrema:bottomKLengthBatch(Attribute, windowLength, Kvalue)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>bottomKLengthBatch</code> counts the frequency of different values of a specified attribute inside a batch window, and emits the lowest (k) number of frequency values.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the frequency is counted. The attribute type can be <code>int</code>, <code>long</code>, <code>float</code>, <code>double</code>, <code>string</code>, <code>bool</code> or <code>object</code>.</li>
<li><strong><code>windowLength</code></strong>: The length of the window. This should be specified as an integer value.</li>
<li><strong><code>Kvalue</code></strong>: The number of bottom frequencies required. This should be specified as an integer value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The bottom K frequency values are emitted per batch.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream inputStream (item string, price long);</code></p>
<br />

<p><code>info(name = 'query1')</code></p>
<p><code>from inputStream#extrema:bottomKLengthBatch(item, 6, 3)</code></p>
<code>insert all events into outputStream;)</code></td>
</tr>
</tbody>
</table>

### topKLength Batch

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>extrema:topKLengthBatch(Attribute, windowLength, Kvalue)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>topKLengthBatch</code> counts the frequency of different values of a specified attribute inside a batch window, and emits the highest (k) number of frequency values.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the frequency is counted. The attribute type can be <code>int</code>, <code>long</code>, <code>float</code>, <code>double</code>, <code>string</code>, <code>bool</code> or <code>object</code>.</li>
<li><strong><code>windowLength</code></strong>: The length of the window. This should be specified as an integer value.</li>
<li><strong><code>Kvalue</code></strong>: The number of top frequencies required. This should be specified as an integer value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The top K frequency values are emitted per batch.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream inputStream (item string, price long);</code></p>
<br />

<p><code>info(name = 'query1')</code></p>
<p><code>from inputStream#extrema:topKLengthBatch(item, 6, 3)</code></p>
<code>insert all events into outputStream;)</code></td>
</tr>
</tbody>
</table>

### bottomK

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>extrema:bottomK(Attribute,Kvalue)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td> </td>
<td><code>bottomK</code> counts the frequency of different values of a specified attribute, and emits the lowest (k) number of frequency values.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the frequency is counted. The attribute type can be <code>int</code>, <code>long</code>, <code>float</code>, <code>double</code>, <code>string</code>, <code>bool</code> or <code>object</code>.</li>
<li><strong><code>Kvalue</code></strong>: The number of bottom frequencies required. This should be specified as an integer value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The bottom K frequency values are emitted. Events are emitted only if there is a change in the <code>bottomK</code> results for each received chunk of events.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream inputStream (item string, price long);</code></p>
<br />

<p><code>info(name = 'query1')</code></p>
<p><code>from inputStream#extrema:bottomK(item, 3)</code></p>
<code>insert all events into outputStream;)</code></td>
</tr>
</tbody>
</table>

### topK

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>extrema:topK(Attribute,Kvalue)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>topK</code> counts the frequency of different values of a specified attribute, and emits the highest (k) number of frequency values.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the frequency is counted. The attribute type can be <code>int</code>, <code>long</code>, <code>float</code>, <code>double</code>, <code>string</code>, <code>bool</code> or <code>object</code>.</li>
<li><strong><code>Kvalue</code></strong>: The number of top frequencies required. This should be specified as an integer value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The top K frequency values are emitted. Events are emitted only if there is a change in the <code>topK</code> results for each received chunk of events.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream inputStream (item string, price long);</code></p>
<br />

<p><code>info(name = 'query1')</code></p>
<p><code>from inputStream#extrema:topK(item, 3)</code></p>
<code>insert all events into outputStream;)</code></td>
</tr>
</tbody>
</table>

### bottomKTimeBatch

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>extrema:bottomKTimeBatch(Attribute,timeWindow,Kvalue)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>bottomKTimeBatch</code> counts the frequency of different values of a specified attribute inside a time window, and emits the lowest (k) number of frequency values.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the frequency is counted. The attribute type can be <code>int</code>, <code>long</code>, <code>float</code>, <code>double</code>, <code>string</code>, <code>bool</code> or <code>object</code>.</li>
<li><code>timeWindow</code>: The time window during which the frequency should be calculated.</li>
<li><strong><code>Kvalue</code></strong>: The number of bottom frequencies required. This should be specified as an integer value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The bottom K frequency values are emitted. Events are emitted only if there is a change in the <code>bottomK</code> results for each received chunk of events.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream inputStream (item string, price long);</code></p>
<p><code>from inputStream#extrema:bottomKTimeBatch(item, 1 sec,  3)</code></p>
<code>insert all events into outputStream;)</code></td>
</tr>
</tbody>
</table>

### topKTimeBatch

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>extrema:topKTimeBatch(Attribute,timeWindow,Kvalue)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>topKTimeBatch</code> counts the frequency of different values of a specified attribute inside a time window, and emits the highest (k) number of frequency values.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the frequency is counted. The attribute type can be <code>int</code>, <code>long</code>, <code>float</code>, <code>double</code>, <code>string</code>, <code>bool</code> or <code>object</code>.</li>
<li><code>timeWindow</code>: The time window during which the frequency should be calculated.</li>
<li><strong><code>Kvalue</code></strong>: The number of top frequencies required. This should be specified as an integer value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The top K frequency values are emitted. Events are not emitted if there are no changes in the topK results after the last chunk of events received.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream inputStream (item string, price long);</code></p>
<p><code>from inputStream#extrema:topKTimeBatch(item, 1 sec,  3)</code></p>
<code>insert all events into outputStream;</code></td>
</tr>
</tbody>
</table>

### maxByLengthBatch

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>window.extrema:maxByLengthBatch(Attribute, BatchLength)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>maxByLengthBatch</code> calculates the maximum value of a specified attribute inside a batch window and emits it.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the maximum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, <code>LONG</code> or <code>STRING</code>.</li>
<li><strong><code>BatchLength</code></strong>: The length of the batch involved. This should be specified as an <code>INT</code> value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The event with the maximum value for the given attribute in the specified batch window is returned.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, price float, volume int);</code></p>
<p><code>from cseEventStream#window.extrema:maxByLengthBatch(price, 4) select symbol,price,volume </code></p>
<code>insert into outputStream ;</code></td>
</tr>
</tbody>
</table>

### minByLengthBatch

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>window.extrema:minByLengthBatch(Attribute, BatchLength)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>minByLengthBatch</code> calculates the minimum value of a specified attribute within a batch window and emits it.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the minimum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, <code>LONG</code> or <code>STRING</code>.</li>
<li><strong><code>BatchLength</code></strong>: The length of the batch involved. This should be specified as an <code>INT</code> value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The event with the minimum value for the given attribute in the specified batch window is returned.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, price float, volume int);</code></p>
<p><code>from cseEventStream#window.extrema:minByLengthBatch(price, 4) select symbol,price,volume </code></p>
<code>insert into outputStream ;</code></td>
</tr>
</tbody>
</table>

### maxByLength

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>window.extrema:minByLength(Attribute, SlidingWindowLength)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>minByLength</code> calculates the maximum value of a specified attribute, and emits it.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the maximum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, <code>LONG</code> or <code>STRING</code>.</li>
<li><strong><code>SlidingWindowLength</code></strong>: The length of the sliding window observed. This should be specified as an <code>INT</code> value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The event with the maximum value for the given attribute in the specified sliding window is returned.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, price float, volume int);</code></p>
<p><code>from cseEventStream#window.extrema:maxByLength(price, 4) select symbol,price,volume </code></p>
<code>insert into outputStream ;</code></td>
</tr>
</tbody>
</table>

### minByLength

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>window.extrema:minByLength(Attribute, SlidingWindowLength)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>minByLength calculates the minimum value of a specified attribute and emits it.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the minimum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, <code>LONG</code> or <code>STRING</code>.</li>
<li><strong><code>SlidingWindowLength</code></strong>: The length of the sliding window observed. This should be specified as an <code>INT</code> value.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The event with the minimum value for the given attribute in the specified sliding window is returned.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, price float, volume int);</code></p>
<p><code>from cseEventStream#window.extrema:minByLength(price, 4) select symbol,price,volume </code></p>
<code>insert into outputStream ;</code></td>
</tr>
</tbody>
</table>

 

### maxByTimeBatch

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>window.extrema:maxByTimeBatch(Attribute, TimeBatchLength)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>maxByTimeBatch calculates the maximum value of a specified attribute within a time window, and emits it.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the maximum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, <code>LONG</code> or <code>STRING</code>.</li>
<li><code>TimeBatchLength</code>: The length of the time window observed.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The event with the maximum value for the given attribute within the specified time window is returned.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, price float, volume int);</code></p>
<p><code>from cseEventStream#window.extrema:maxByTimeBatch(price, 1 sec) select symbol,price,volume </code></p>
<code>insert into outputStream ;</code></td>
</tr>
</tbody>
</table>

 

### minByTimeBatch

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>window.extrema:minByTimeBatch(Attribute, TimeBatchLength)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>minByTimeBatch</code> calculates the minimum value of a specified attribute within a time window and emits it.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the maximum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, <code>LONG</code> or <code>STRING</code>.</li>
<li><code>TimeBatchLength</code>: The length of the time window observed.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The event with the minimum value for the given attribute within the specified time window is returned.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, price float, volume int);</code></p>
<p><code>from cseEventStream#window.extrema:minByTimeBatch(price, 1 sec) select symbol,price,volume </code></p>
<code>insert into outputStream ;</code></td>
</tr>
</tbody>
</table>

 

### maxByTime

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>window.extrema:maxByTime(Attribute, TimeWindowLength)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>maxByTime</code> calculates the maximum value of a specified attribute within a sliding time window and emits it.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the maximum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, <code>LONG</code> or <code>STRING</code>.</li>
<li><strong><code>TimeWindowLength</code></strong>: The length of the sliding time window observed.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The event with the maximum value for the given <strong><code>Attribute</code></strong> is returned. This output is updated for every event arrival and expiry during the <strong><code>TimeWindowLength</code></strong> specified.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, price float, volume int);</code></p>
<p><code>from cseEventStream#window.extrema:maxByTime(price, 1 sec) select symbol,price,volume </code></p>
<code>insert into outputStream ;</code></td>
</tr>
</tbody>
</table>

### minByTime

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>window.extrema:minByTime(Attribute, TimeWindowLength)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>minByTime</code> calculates the minimum value of a specified attribute within a sliding time window and emits it.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the minimum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, <code>LONG</code> or <code>STRING</code>.</li>
<li><strong><code>TimeWindowLength</code></strong>: The length of the sliding time window observed.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>The event with the minimum value for the given <strong><code>Attribute</code></strong> is returned. This output is updated for every event arrival and expiry during the <strong><code>TimeWindowLength</code></strong> specified.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, price float, volume int);</code></p>
<p><code>from cseEventStream#window.extrema:maxByTime(price, 1 sec) select symbol,price,volume </code></p>
<code>insert into outputStream ;</code></td>
</tr>
</tbody>
</table>

### kalmanMinMax

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code> extrema:kalmanMinMax(Attribute, Q, R, WindowSize, ExtremaType)</code></p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>kalmanMinMax </code>uses the <code>kalman</code> filter to smooth the time series values in the given window size, and then determine the maxima and/or minima of that set of values.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the minimum and/or maximum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, or <code>LONG.</code></li>
<li><strong><code>Q</code></strong>: The standard deviation of the process noise.</li>
<li><code>R</code>: The standard deviation of the measurement noise.</li>
<li><strong><code>WindowSize</code></strong>: The length of the window within which the minimum and/or the maximum value for the given window should be identified.</li>
<li><strong>ExtremaType</strong>: This can be min, max or minmax.
<ul>
<li><code>min</code>: If this is specified, minimum values are identified within the given window length, and they are returned with <code>min</code> as their extrema type.</li>
<li><code>max</code>: If this is specified, maximum values are identified within the given window length, and they are returned with <code>max</code> as their extrema type.</li>
<li><code>minmax</code>: If this is specified, both minimum and maximum values are identified within the given window length and returned. The extrema type is specified as <code>min</code> for the minimum events, and as <code>max</code> for the maximum events.<br />
</li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>Returns the events with the minimum and/or maximum for the specified attribute within the given window length, with the extrema type as <code>min</code> or <code>max</code> as relevant.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code class="sourceCode sql">inputStream#<span class="ch">:kalmanMinMax</span>(price, <span class="fl">0.000001</span>,<span class="fl">0.0001</span>, <span class="dv">25</span>, </code><code class="sourceCode sql"><span class="st">&#39;min&#39;</span></code>) returns the minimum values for a set of <code>price</code> values.</td>
</tr>
</tbody>
</table>

### kernalMinMax

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>extrema:kernelMinMax(Attribute, Bandwidth, WindowSize, ExtremaType)</code></p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><code>kernalMinMax</code> uses Gaussian Kernel to smooth the time series values in the given window size, and then determine the maxima and minima of that set of values.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>Attribute</code></strong>: The attribute of which the minimum and/or maximum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, or <code>LONG.</code></li>
<li><code>Bandwidth</code>: The bandwidth of the Gaussian Kernel calculation.</li>
<li><code>Window size</code>: The length of the window within which the minimum and/or the maximum value for the given window should be identified.</li>
<li><code>Extrema type</code>: This can be <code>min</code>, <code>max</code> or <code>minmax.</code><br />

<ul>
<li><code>min</code>: If this is specified, minimum values are identified within the given window length, and they are returned with <code>min</code> as their extrema type.</li>
<li><code>max</code>: If this is specified, maximum values are identified within the given window length, and they are returned with <code>max</code> as their extrema type.</li>
<li><code>minmax</code>: If this is specified, both minimum and maximum values are identified within the given window length and returned. The extrema type is specified as <code>min</code> for the minimum events, and as <code>max</code> for the maximum events.</li>
</ul>
<code></code></li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>Returns the events with the minimum and/or maximum for the specified attribute within the given window length, with the extrema type as <code>min</code> or <code>max</code> as relevant.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p>The following returns the maximum values for a set of <code>price</code> values.</p>
<p><code class="sourceCode sql"><span class="kw">from</span></code> <code class="sourceCode sql">inputStream#timeseries<span class="ch">:kernelMinMax</span>(price, <span class="dv">3</span>, <span class="dv">7</span>, ‘</code><code class="sourceCode sql"><span class="fu">max</span></code><code class="sourceCode sql">’)</code></p>
<div class="line number2 index1 alt1">
<code class="sourceCode sql"><span class="kw">select</span></code> <code class="sourceCode sql"><span class="op">*</span></code>
</div>
<div class="line number3 index2 alt2">
<code class="sourceCode sql"><span class="kw">insert</span></code> <code class="sourceCode sql"><span class="kw">into</span></code> <code class="sourceCode sql">outputStream;</code>
</div></td>
</tr>
</tbody>
</table>

### minMax

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>extrema:minMax(Attribute, MaxPreBound, MaxPostBound, PreBoundChange, PostBoundChange, ExtremaType)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td> StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><p>minMax finds the minimum and/or the maximum value within a given length window (<code>maxPreBound</code>+<code>maxPostBound</code>), where following conditions are met.</p>
<p>For minimum:</p>
<ul>
<li>An event where the value for the specified <strong><code>attribute</code></strong> is greater by the percentage specified as the <strong><code>preBoundChange</code></strong> should have arrived prior to the event with the minimum value, within the maxPreBound length window.</li>
</ul>
<ul>
<li>An event where the value for the specified <strong><code>attribute</code></strong> is greater by the percentage specified as the <strong><code>postBoundChange</code></strong> should have arrived after the event with the minimum value, within the <code>maxPostBound</code> length window.</li>
</ul>
<p> </p>
<p>For maximum:</p>
<ul>
<li>An event where the value for the specified <strong><code>attribute</code></strong> is less by the percentage specified as the <strong><code>preBoundChange</code></strong> should have arrived prior to the event with the maximum value, within the <strong><code>maxPreBound </code></strong>length window.</li>
<li>An event where the value for the specified <strong><code>attribute</code></strong> is less by the percentage specified as the <strong><code>postBoundChange</code></strong> should have arrived after the event with the maximum value, within the <code>maxPostBound</code> length window.</li>
</ul>
<p> </p></td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong>Attribute</strong>: The attribute of which the minimum and/or maximum value is required. The data type of the value for this parameter can be <code>INT</code>,<code> FLOAT</code>, <code>DOUBLE</code>, or <code>LONG.</code></li>
<li><strong><code>MaxPreBound</code></strong>: The maximum pre window length to be considered (before the min/max event).</li>
<li><strong><code>MaxPostBound</code></strong>: The maximum post window length to be considered (after the min/max event).</li>
<li><code>PreBoundChange</code>: The threshold, pre-bound change percentage.</li>
<li><strong><code>PostBoundChang</code></strong>e: The threshold, post-bound change percentage.</li>
<li><code>ExtremaType</code>: This can be <code>min</code>, <code>max</code> or <code>minmax</code>.
<ul>
<li><code>min</code>: If this is specified, minimum values are identified within the given window length, and they are returned with <code>min</code> as their extrema type.</li>
<li><code>max</code>: If this is specified, maximum values are identified within the given window length, and they are returned with <code>max</code> as their extrema type.</li>
<li><code>minmax</code>: If this is specified, both minimum and maximum values are identified within the given window length and returned. The extrema type is specified as <code>min</code> for the minimum events, and as <code>max</code> for the maximum events.</li>
</ul></li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td><p>Returns the events with the minimum and/or maximum for the specified attribute within the given window length, with the extrema type as <code>min</code> or <code>max</code> as relevant. These events are returned with the following additional parameters.</p>
<ul>
<li><strong><code>preBound</code></strong>: The actual distance between the minimum/maximum value and the threshold value. This value should be within the <code>MaxPreBound</code> window.</li>
<li><strong><code>postBound</code></strong>: The actual distance between the minimum/maximum value and the threshold value. This value should be within the <code>MaxPostBound</code> window.</li>
</ul></td>
</tr>
<tr class="even">
<td>Example</td>
<td><ul>
<li><p>The following returns the maximum values found within a set of price values.<br />
</p>
<p><code>from inputStream#timeseries:minMax(price, 4, 4, 1, 2, 'max')</code></p>
<p><code>select *</code></p>
<p><code>insert into outputStream;  </code></p></li>
<li><p>The following returns the minimum values found within a set of price values.<br />
</p>
<p><code>from inputStream#timeseries:minMax(price, 4, 4, 1, 2, 'min')</code></p>
<p><code>select *</code></p>
<p><code>insert into outputStream;  </code></p></li>
<li><p>The following returns both the minimum values and the maximum values found within a set of price values.<br />
</p>
<p><code>from inputStream#timeseries:minMax(price, 4, 4, 1, 2, 'min')</code></p>
<p><code>select *</code></p>
<p><code>insert into outputStream; </code></p></li>
</ul></td>
</tr>
</tbody>
</table>
