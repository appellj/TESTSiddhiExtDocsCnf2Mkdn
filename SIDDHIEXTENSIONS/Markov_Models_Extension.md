# Markov Models Extension

The Markov Models extension allows abnormal patterns relating to user
activity to be detected when carrying out real time analysis. There are
two approaches for using this extension. Click on the relevant tab for
detailed information about the required approach.

-   [**Using an existing matrix**](#270c9a9311d344bb90ab54ffe4c1926a)
-   [**Building a new matrix**](#e1730668710b4cdaac1a2d18f42258b2)

You can input an existing Markov matrix as a csv file. It should be a N
x N matrix, and the first row should include state names as shown in the
following samples. The rows below that indicate the transition
probabilities/transition counts for all the possible state transitions.

``` java
testState01,testState02,testState03
0.1,0.6,0.3
0.3,0.5,0.2
0.6,0.3,0.1
```

``` java
testState01,testState02,testState03
2,12,6
6,10,4
12,6,2
```

### Syntax

The following is the syntax for a query with the Markov Models extension
using an existing matrix.

``` sql
markov:markovChain(<String> id, <String> state, <int|long|time> durationToKeep, <double> alertThreshold, <String> markovMatrixStorageLocation, <boolean> train)
```

### Input parameters

The following are the input parameters for this extension.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required/Optional</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>id</code></td>
<td>Required</td>
<td>The ID of the particular user or object being analyzed.</td>
</tr>
<tr class="even">
<td><code>state</code></td>
<td>Required</td>
<td>The current state of the ID.</td>
</tr>
<tr class="odd">
<td><code>durationToKeep</code></td>
<td>Required</td>
<td>The maximum time duration to be considered for a continuous state change of a particular ID.</td>
</tr>
<tr class="even">
<td><code>alertThreshold</code></td>
<td>Required</td>
<td><p>The alert threshold probability.</p></td>
</tr>
<tr class="odd">
<td><code>markovMatrixStorageLocation</code></td>
<td>Required</td>
<td><p>The location of the CSV file that contains the existing Markov matrix to be used.</p></td>
</tr>
<tr class="even">
<td><code>train</code></td>
<td>Optional</td>
<td><p>If this is set to <code>true</code>, event values are used to train the Markov matrix. If this is set to <code>false</code>, the Markov matrix values remain the same.</p></td>
</tr>
</tbody>
</table>

### Output parameters

The following are the output parameters for this extension.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>lastState</code></p></td>
<td>Last state</td>
<td>The previous state of the particular ID.</td>
</tr>
<tr class="even">
<td><code>transitionProbability</code></td>
<td>Transition probability</td>
<td>The transition probability between the previous state and the current state for a particular ID.</td>
</tr>
<tr class="odd">
<td><code>notify</code></td>
<td>notify</td>
<td>This signifies a notification that indicates that the transition probability is less than or equal to the alert threshold probability.</td>
</tr>
</tbody>
</table>

### Example

The following returns notifications to indicate whether a transition
probability is less than or equal to 0.2 according to the Markov matrix
you have provided.

``` sql
define stream InputStream (id string, state string);
from InputStream#markov:markovChain(id, state, 60 min, 0.2, “markovMatrixStorageLocation”, false)
select id, lastState, state, transitionProbability, notify
insert into OutputStream;
```

This approach involves using a reasonable amount of incoming data to
train a Markov matrix and then using it to create notifications.

### Syntax

The following is the syntax for a query with the Markov Models extension
using a matrix newly built using incoming data.

``` sql
markov:markovChain(<String> id, <String> state, <int|long|time> durationToKeep, <double> alertThreshold, <int|long> notificationsHoldLimit, <boolean> train)
```

### Input parameters

The following are the input parameters for this extension.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Required/Optional</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>id</code></td>
<td>Required</td>
<td>The ID of the particular user or object being analyzed.</td>
</tr>
<tr class="even">
<td><code>state</code></td>
<td>Required</td>
<td>The current state of the ID.</td>
</tr>
<tr class="odd">
<td><code>durationToKeep</code></td>
<td>Required</td>
<td>The maximum time duration to be considered for a continuous state change of a particular ID.</td>
</tr>
<tr class="even">
<td><code>alertThreshold</code></td>
<td>Required</td>
<td><p>The alert threshold probability.</p></td>
</tr>
<tr class="odd">
<td><code>notificationsHoldLimitor</code></td>
<td>Required</td>
<td><p>The number of events that should be received before the matrix starts triggering notifications.</p></td>
</tr>
<tr class="even">
<td><code>train</code></td>
<td>Optional</td>
<td><p>If this is set to <code>true</code>, event values are used to train the Markov matrix. If this is set to <code>false</code>, the Markov matrix values remain the same.</p></td>
</tr>
</tbody>
</table>

### Output parameters

The following are the output parameters for this extension.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><code>lastState</code></p></td>
<td>Last state</td>
<td>The previous state of the particular ID.</td>
</tr>
<tr class="even">
<td><code>transitionProbability</code></td>
<td>Transition probability</td>
<td>The transition probability between the previous state and the current state for a particular ID.</td>
</tr>
<tr class="odd">
<td><code>notify</code></td>
<td>notify</td>
<td>This signifies a notification that indicates that the transition probability is less than or equal to the alert threshold probability.</td>
</tr>
</tbody>
</table>

### Example

The following query returns notifications that indicate whether a
transition probability is less than or equal to 0.1 according to the
Markov matrix that is build using incoming data itself. This starts
sending notifications after the first 500 events arrive.

``` sql
define stream InputStream (id string, state string, train bool);
from InputStream#markov:markovChain(id, state, 60 min, 0.1, 500, train)
select id, lastState, state, transitionProbability, notify
insert into OutputStream;
```
