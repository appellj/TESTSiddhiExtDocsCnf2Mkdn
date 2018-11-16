# UniqueTime Window

-   [Introduction](#UniqueTimeWindow-Introduction)
-   [Downloading the
    extension](#UniqueTimeWindow-Downloadingtheextension)
-   [Deploying the artifacts](#UniqueTimeWindow-Deployingtheartifacts)
-   [Sample query](#UniqueTimeWindow-Samplequery)

### Introduction

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>&lt;event&gt;  unique:time (&lt;string|int|long|bool|double&gt;  attribute,  windowTime )</code> </p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Window</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This window returns unique events within the specified time based on the given attributes.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><p><strong><code>attribute</code></strong>: The attribute that should be checked for uniqueness.</p>
<p><strong><code>windowTime</code></strong>: The sliding time period for which the window should hold events.</p></td>
</tr>
<tr class="odd">
<td>Return Type</td>
<td>Returns current and expired events.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>unique(ip,3 sec)</code> returns the latest event that arrives for each unique IP within the last 3 seconds.<code></code></td>
</tr>
</tbody>
</table>

### Downloading the extension

This extension and the other artifacts required to use it can be
downloaded from [here](https://store.wso2.com/).

### Deploying the artifacts

Place the `org.wso2.extension.siddhi.window.uniquetime-1.0.0.jar` you
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

@Import('TestUniqueTimeWindow:1.0.0')
define stream UniqueTimeIN (timeStamp long, a string, ip string);

@Export('TestUniqueTimeWindowOut:1.0.0')
define stream UniqueTimeOUT (a string, ip string);

from UniqueTimeIN#window.unique:time(ip,3 sec)
select a, ip
insert expired events into UniqueTimeOUT;
```
