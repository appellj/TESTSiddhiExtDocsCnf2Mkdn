# Reorder Extension

Reorder extension is implemented using the `K-Slack` algorithm.
The `K-Slack` Siddhi extension is used for reordering events from an
unordered event stream. The following is an example of a query with
the `reorder` extension.

 

``` sql
@info(name = 'query1') 
from inputStream#reorder:kslack(eventTimestamp) 
select eventTimestamp, price, volume 
insert into outputStream;
```

There are several important variations of the K-slack API of which the
details are described below

-   [K-Slack function](#ReorderExtension-K-Slackfunction)

### K-Slack function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>&lt;bool&gt; reorder:kslack(&lt;long&gt; timestamp)</code></p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This is the most basic version. The events are sorted by the <code>           timestamp         </code> parameter.</td>
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
<td><p><code>&lt;bool&gt; reorder:kslack(&lt;long&gt; timestamp, &lt;long&gt; timeOut )</code></p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>The second argument shown in the above syntax corresponds to a fixed time-out value set at the beginning of the process. Once the time-out value expires, the extension drains all the events that are buffered within the reorder extension to outside. The time out has been implemented internally using a timer. The events buffered within the extension are released each time the timer ticks.</td>
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
<td><pre><code>&lt;bool&gt; reorder:kslack(&lt;long&gt; timestamp, &lt;long&gt; timeOut, &lt;long&gt; maxValue )</code></pre></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>The third argument in the above syntax is the maximum value for K. This is the amount to which the K value of the K-Slack algorithm will be increased.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><ul>
<li><code>kslack(timestamp, -1l, 1000000)</code><br />
In the above example, the algorithm execution starts when K=0 and it gets increased up to 1000000. The value of the <code>K-slack</code> does not increase from that point onwards. Hence, this leads to lower latency compared to the version shown in the first (i.e., single parameter) example of this list. Note that the second argument is set to <code>-1l</code> which effectively disables the timer based draining of the internal buffer.</li>
<li><p><code>kslack(timestamp, 1000l, 1000000)</code><br />
The above is another variation of the third category. Here, a time-out value is specified for the second argument (i.e. 1000 ms). In this case, the K-slack algorithm buffers events until the 1000ms time period expires. The maximum K value is 1000000. The K-value cannot exceed the specified amount.</p></li>
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
<td><p><code>&lt;bool&gt; </code> <strong>reorder:kslack</strong> (&lt;long&gt; timestamp, &lt;long&gt; timeOut, &lt;bool&gt; expireFlag )</p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>The fourth argument in the above syntax is a flag that indicates whether the out-of order events that appear after the expiration of the K-slack window should be discarded or not.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>kslack(timestamp, -1l, true) </code></td>
</tr>
</tbody>
</table>
