# Priority Extension

PriorityStreamProcessor keeps track of the priority of events in a
stream. This stream processor requires three arguments which are as
follows.

-   A unique key variable to identify the event.
-   A priority variable that contains the priority increment.
-   A timeout in constant to decrease the priority by one after the
    given timeout.

 

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>#priority:time(variable, priority, timeout)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Parameters</td>
<td><ul>
<li><strong><code>variable</code></strong>: A unique key variable to identify the event.</li>
<li><strong><code>priority</code></strong>: The priority variable that contains the priority increment.</li>
<li><strong><code>return</code></strong>: Timeout in constant to decrease the priority by one after the given timeout.</li>
</ul></td>
</tr>
<tr class="even">
<td>Return</td>
<td><p>When an event with a new unique key arrives, the PriorityStreamProcessor checks the priority and if the priority is 0, the event is sent without being stored internally. If an event has a priority greater than 0, it is stored in the Stream Processor, and the current priority is injected into that event.</p>
<p>When an event with the existing priority key arrives, it is stored as a recent event, the priority is increased by the priority of the received event, and the <code>priorityKey</code> and the <code>currentPriority</code> are injected into the event.</p>
<p>After every given timeout, the priority of each event is reduced by 1, and the updated priority is sent out with the last known attributes of those events. This continues until their priority is reduced to 0.</p>
<p>When an event with an existing ID and a large negative priority arrives, the output is 0 and not a negative priority.</p></td>
</tr>
<tr class="odd">
<td>Example</td>
<td><p><code>define stream cseEventStream (symbol string, priority long, volume int);</code></p>
<p><code>@info(name = 'query1') </code></p>
<p><code>from cseEventStream#priority:time(symbol, priority, 1 sec)</code></p>
<p><code>select *</code></p>
<code>insert all events into outputStream ;</code></td>
</tr>
</tbody>
</table>
