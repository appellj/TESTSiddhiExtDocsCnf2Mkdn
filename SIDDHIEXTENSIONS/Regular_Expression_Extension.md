# Regular Expression Extension

This extension provides basic RegEx execution capabilities to Siddhi.
Following are the functions of the RegEx extension.

-   [Find function](#RegularExpressionExtension-Findfunction)
-   [Group function](#RegularExpressionExtension-Groupfunction)
-   -   [Looking At
    function](#RegularExpressionExtension-LookingAtfunction)
-   [Matches function](#RegularExpressionExtension-Matchesfunction)

### **Find function**

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;bool&gt; regex:find (&lt;string&gt; regex , &lt;string&gt; inputSequence )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This method attempts to find the next sub-sequence of the  <strong><code>inputSequence</code></strong>  that matches the  <strong><code>regex</code></strong>  pattern. It returns <code>true</code> if such a sub sequence exists, or returns <code>false</code> otherwise.</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>find(&quot;\d\d(.*)WSO2&quot;, &quot;21 products are produced by WSO2 currently&quot;)</code> returns <code>true</code>.</li>
<li><code>find(&quot;\d\d(.*)WSO2&quot;, &quot;21 products are produced currently&quot;)</code> returns <code>false</code>.</li>
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
<td><code>&lt;bool&gt; regex:           find (&lt;string&gt; regex , &lt;string&gt; inputSequence, &lt;int&gt; startingIndex )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This method attempts to find the next sub-sequence of the  <strong><code>inputSequence</code></strong>  that matches the  <strong><code>regex</code></strong>  pattern starting from given index (i.e.  <strong><code>startingIndex</code></strong> ). It returns <code>true</code> if such a sub sequence exists, or returns <code>false</code> otherwise.</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>find(&quot;\d\d(.*)WSO2&quot;, &quot;21 products are produced within 10 years by WSO2 currently by WSO2 employees&quot;,  30)</code> returns <code>true</code>.</li>
<li><code>find(&quot;\d\d(.*)WSO2&quot;, &quot;21 products are produced within 10 years by WSO2 currently by WSO2 employees&quot;, 35)</code> returns <code>false</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

**  
**

### **Group function**

|                |                                                                                                                                                                                                                                                                                                                                |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> regex:           group (<string> regex , <string> inputSequence , <int>  groupId )`                                                                                                                                                                                                                                  |
| Extension Type | Function                                                                                                                                                                                                                                                                                                                       |
| Description    | Returns the input sub-sequence captured by the given group during the previous match operation. Returns `null` if no sub-sequence was found during the previous match operation. For more information about the match operation, see [matches](https://docs.wso2.com/display/CEP420/Siddhi+Extensions#SiddhiExtensions-match). |
| Example        |  `group("(\d\d)(.*)(WSO2.*)", "21 products are produced within 10 years by WSO2 currently by WSO2 employees", 3)` returns `"WSO2 employees"`.                                                                                                                                                                                  |

### **Looking At function**

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;string&gt; regex:           lookingAt (&lt;string&gt; regex , &lt;string&gt; inputSequence )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This method attempts to match the  <strong><code>inputSequence</code></strong>  against the  <strong><code>regex</code></strong>  pattern starting at the beginning.</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>lookingAt(&quot;\d\d(.*)WSO2&quot;, &quot;21 products are produced by WSO2 currently in Sri Lanka&quot;</code>) returns <code>true</code>.</li>
<li><code>lookingAt(&quot;WSO2(.*)middleware(.*)&quot;, &quot;sample test string and WSO2 is situated in trace and its a middleware company&quot;)</code> returns <code>false</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

**  
**

### **Matches function**

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;string&gt; regex:           matches (&lt;string&gt; regex , &lt;string&gt; inputSequence )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This method attempts to match the entire  <strong><code>inputSequence</code></strong>  against the  <strong><code>regex</code></strong>  pattern.</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>matches(&quot;WSO2(.*)middleware(.*)&quot;, &quot;WSO2 is situated in trace and its a middleware company&quot;)</code> returns <code>true</code>.</li>
<li><code>matches(&quot;WSO2(.*)middleware&quot;, &quot;WSO2 is situated in trace and its a middleware company&quot;)</code> returns <code>false</code>.</li>
</ul></td>
</tr>
</tbody>
</table>
