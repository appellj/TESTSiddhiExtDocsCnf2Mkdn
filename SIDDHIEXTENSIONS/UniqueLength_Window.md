# UniqueLength Window

-   [Introduction](#UniqueLengthWindow-Introduction)
-   [Downloading the
    extension](#UniqueLengthWindow-Downloadingtheextension)
-   [Deploying the artifacts](#UniqueLengthWindow-Deployingtheartifacts)
-   [Sample query](#UniqueLengthWindow-Samplequery)

### Introduction

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;event&gt; unique:length (&lt;string|int|long|bool|double&gt; attribute, &lt;int&gt; windowLength )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Window</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This window returns unique events within the specified length based on the given attributes.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><p><strong><code>attribute</code></strong>: The attribute that should be checked for uniqueness.</p>
<p><strong><code>windowLength</code></strong>: The number of events that should be included in a sliding length window.</p></td>
</tr>
<tr class="odd">
<td>Return Type</td>
<td>Returns current and expired events.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>unique(ip,3)</code> returns the last event that arrives for each unique IP out of the last 3 events.</td>
</tr>
</tbody>
</table>

### Downloading the extension

This extension and the other artifacts required to use it can be
downloaded from [here](https://store.wso2.com/).

### Deploying the artifacts

Place the `org.wso2.extension.siddhi.window.uniquelength-1.0.0.jar` you
downloaded in
the &lt;CEP\_HOME&gt;/repository/components/dropins directory.

### Sample query

The following is a sample query for this extension.

Before writing this query in an execution plan, the event streams used
in the query as the input and output streams should be defined. For
detailed instructions to define event streams, see [Understanding Event
Streams](http://docs.wso2.com/complex-event-processor/Understanding%20Event%20Streams).

**Sample Query**

``` java
/* Enter a unique ExecutionPlan */
@Plan:name('ExecutionPlan')

/* Enter a unique description for ExecutionPlan */
-- @Plan:description('ExecutionPlan')

/* define streams/tables and write queries here ... */

@Import('TestUniqueLengthWindow:1.0.0')
define stream UniqueLengthIN (timeStamp long, a string, ip string);

@Export('TestUniqueLengthWindowOut:1.0.0')
define stream UniqueLengthOUT (a string, ip string);

from UniqueLengthIN#window.unique:length(ip,3)
select a, ip
insert expired events into UniqueLengthOUT;
```
