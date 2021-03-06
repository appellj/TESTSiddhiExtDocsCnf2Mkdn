# JavaScript Extension

This extension allows you to include JavaScript functions within the
Siddhi Query Language.

-   [JavaScript function](#JavaScriptExtension-JavaScriptfunction)

### JavaScript function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>define function &lt;function name&gt;[&lt;language name&gt;] return &lt;return type&gt; {</code></p>
<p><code>    &lt;operation of the function&gt;</code></p>
<code>};</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Eval Script</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>The <strong><code>&lt;operation of the function&gt;</code></strong> is an operation of the <strong><code>&lt;function name&gt;</code></strong> that is defined in the <strong><code>&lt;language name&gt;</code></strong> language, and the output is returned in the <strong><code>&lt;return Type&gt;</code></strong> specified.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>function</code><code> name</code></strong>: The name of the function.</li>
<li><strong><code>language name</code></strong>: The language of the script. In this scenario, it should be JavaScript.</li>
<li><strong><code>return type</code></strong>: The return type of the function (int, long, float, double, string, bool or object).</li>
<li><strong><code>operation of the</code> <code>function</code></strong>: The logic of the function.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Example</td>
<td><p><code>define function concatFunction[JavaScript] return string {</code></p>
<p><code>    var str1 = data[0];</code></p>
<p><code>    var str2 = data[1];</code></p>
<p><code>    var responce = str1 + str2</code></p>
<p><code>    return responce;</code></p>
<p><code>};</code></p>
<p>The above function concatenates two strings and returns the output. The input parameters are automatically input as arrays, and they can be accessed as <code>data[1]</code> and <code>data[0]</code>.</p>
<p>A stream can be defined as follows.</p>
<p><code>define stream TempStream(deviceID long, roomNo int, temp double);</code></p>
<p>The eval script defined above can be used in this stream as follows.</p>
<p><code>from TempStream</code></p>
<p><code>select concatFunction(roomNo,deviceID) as id, temp  </code></p>
<p><code>insert into DeviceTempStream;</code></p></td>
</tr>
</tbody>
</table>
