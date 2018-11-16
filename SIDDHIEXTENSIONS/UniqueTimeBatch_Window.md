# UniqueTimeBatch Window

-   [Introduction](#UniqueTimeBatchWindow-Introduction)
-   [Downloading the
    extension](#UniqueTimeBatchWindow-Downloadingtheextension)
-   [Deploying the
    artifacts](#UniqueTimeBatchWindow-Deployingtheartifacts)
-   [Sample query](#UniqueTimeBatchWindow-Samplequery)

### Introduction

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p>unique:timeBatch ( attribute, uniquewindowTime,  isFirstUniqueEnabled )</p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Window</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>A unique length batch (tumbling)  window that holds a number of unique events within the value specified for the <code>windowTime</code> parameter. The window is updated each time a batch of events that equals the number specified for the <code>uniquewindowTime</code> parameter arrives.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><p><strong><code>attribute</code></strong>: The attribute that should be checked for uniqueness.</p>
<p><code>uniquewindowTime</code>: The sliding time period for which the window should hold events.</p>
<p><strong>isFirstUniqueEnabled:  </strong> Default value is <strong>false</strong> means last unique events if we need to keep first unique events it should <strong>true</strong>.</p></td>
</tr>
<tr class="odd">
<td>Return Type</td>
<td>Returns current and expired events.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>unique:timeBatch(ip,3 sec)</code> holds the latest event that arrives for each unique IP within each 3 seconds.<code></code></td>
</tr>
</tbody>
</table>

### Downloading the extension

This extension and the other artifacts required to use it can be
downloaded from [here](https://store.wso2.com/).

### Deploying the artifacts

Place the `org.wso2.extension.siddhi.window.uniquetimebatch-1.0.0.jar`
you downloaded in
the `<CEP_HOME>/repository/components/dropins` directory.

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

@Import('TestUniqueTimeBatchWindow:1.0.0')
define stream UniqueTimeBatchIN (timeStamp long, a string, ip string);

@Export('TestUniqueTimeBatchWindowOut:1.0.0')
define stream UniqueTimeBatchOUT (a string, ip string);

from UniqueTimeBatchIN#window.unique:timeBatch(ip,3 sec)
select a, ip
insert expired events into UniqueTimeBatchOUT;
```

 

558

125

148

212
