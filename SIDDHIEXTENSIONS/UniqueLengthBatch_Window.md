# UniqueLengthBatch Window

-   [Introduction](#UniqueLengthBatchWindow-Introduction)
-   [Downloading the
    extension](#UniqueLengthBatchWindow-Downloadingtheextension)
-   [Deploying the
    artifacts](#UniqueLengthBatchWindow-Deployingtheartifacts)
-   [Sample query](#UniqueLengthBatchWindow-Samplequery)

### Introduction

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;event&gt; unique:lengthBatch (&lt;string|int|long|bool|double&gt; attribute, &lt;int&gt; uniquewindowLength, &lt;bool&gt; isFirstUniqueEnabled)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Window</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>A unique length batch (tumbling) window that holds a number of unique events within the number specified for the <code>windowLength</code> parameter. The window is updated each time a batch of events that equals the number specified for the <code>uniquewindowLength</code> parameter arrives.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><p><strong><code>attribute</code></strong>: The attribute that should be checked for uniqueness.</p>
<p><code>uniquewindowLength</code>: The number of events the window should tumble.</p>
<p><strong>isFirstUniqueEnabled:  </strong> Default value is <strong>false</strong> means last unique events if we need to keep first unique events it should <strong>true</strong>. <strong></strong></p></td>
</tr>
<tr class="odd">
<td>Return Type</td>
<td>Returns current and expired events.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>unique:lengthBatch</code>(ip,4) holds the batch of events that are unique to each 4 events.</td>
</tr>
</tbody>
</table>

### Downloading the extension

This extension and the other artifacts required to use it can be
downloaded from [here](https://store.wso2.com/).

### Deploying the artifacts

Place
the `org.wso2.extension.siddhi.window.uniquelengthbatch-1.0.0.jar` you
downloaded in the `<CEP_HOME>/repository/components/dropins` directory.

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

@Import('TestUniqueLengthBatchWindow:1.0.0')
define stream UniqueLengthBatchIN (timeStamp long, a string, ip string);

@Export('TestUniqueLengthBatchWindowOut:1.0.0')
define stream UniqueLengthBatchOUT (a string, ip string);

from UniqueLengthIN#window.unique:lengthBatch(ip,3)
select a, ip
insert expired events into UniqueLengthBatchOUT;
```

 

557

560

97

145

210
