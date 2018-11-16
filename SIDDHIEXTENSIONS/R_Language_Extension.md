# R Language Extension

First you need to setup
the [prerequisites](https://docs.wso2.com/display/CEP420/Installing+R+to+work+with+WSO2+CEP) .

This extension allows you to execute R scripts within Siddhi query.
Following are the functions of the R extension.

-   [Evaluation function](#RLanguageExtension-Evaluationfunction)
-   [Evaluation Source
    function](#RLanguageExtension-EvaluationSourcefunction)

### Evaluation function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>[&lt;int|long|float|double|string|boolean&gt;  output1 ,  &lt;int|long|float|double|string|boolean&gt;   output2, ... ] r:eval   ( &lt;string &gt; script,  &lt;string &gt;  outputAttributes, &lt;int|long|float|double|string|boolean &gt;  input1 , &lt;int|long|float|double|string|boolean&gt; input2 , ... )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This runs the R script for each event and produces  aggregated outputs based on the provided input variable parameters and expected output attributes.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><p><strong><code>script</code></strong> : R script as a string produces aggregated outputs based on the provided input variable parameters and expected output attributes.<br />
<strong><code>outputAttributes</code></strong>  : A set of output attributes separated by commas as string. Each attribute is denoted as <code>&lt;name&gt;&lt;space&gt;&lt;type&gt;</code>. e.g.,<code> 'output1 string, output2 long'</code></p></td>
</tr>
<tr class="odd">
<td>Return Parameters</td>
<td>Output parameters are generated based on the <code>outputAttributes</code> provided.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>eval('totalItems &lt;- sum(items); totalTemp &lt;- sum(temp);', 'totalItems int, totalTemp double', items, temp)</code>, where the data type of <code>items</code> is <code>int</code> and that of <code>temp</code> is <code>double</code>returns <code>[ totalItems, totalTemp ]</code>, where the data type of <code>totalItems</code> is <code>int</code> and that of <code>totalTemp</code> is <code>double</code>.</p>
<div class="code panel pdl" style="border-width: 1px;">
<div class="codeContent panelContent pdl">
<div class="sourceCode" id="cb1" data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence" style="brush: java; gutter: false; theme: Confluence"><pre class="sourceCode java"><code class="sourceCode java"><a class="sourceLine" id="cb1-1" title="1"><span class="at">@info</span>(name = &#39;query1&#39;) </a>
<a class="sourceLine" id="cb1-2" title="2">from dataIn#window.<span class="fu">lengthBatch</span>(<span class="dv">2</span>)#r:<span class="fu">eval</span>(&#39;totalItems &lt;- <span class="fu">sum</span>(items); totalTemp &lt;- <span class="fu">sum</span>(temp);&#39;, &#39;totalItems <span class="dt">int</span>, totalTemp double&#39;, items, temp)</a>
<a class="sourceLine" id="cb1-3" title="3">select *</a>
<a class="sourceLine" id="cb1-4" title="4">insert into dataOut;</a></code></pre></div>
</div>
</div></td>
</tr>
</tbody>
</table>

 

### Evaluation Source function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>[&lt;int|long|float|double|string|boolean&gt;  output1 ,  &lt;int|long|float|double|string|boolean&gt;   output2, ... ] r:eval   ( &lt;string &gt; filePath,  &lt;string &gt;  outputAttributes,&lt;int|long|float|double|string|boolean&gt;  input1 , &lt;int|long|float|double|string|boolean&gt; input2 , ... )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Stream Processor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>This runs the R script loaded from a file to each event and produces aggregated outputs based on the provided input variable parameters and expected output attributes.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><p><strong><code>filePath</code></strong> : The file path of the R script where this script uses the input variable parameters and produces the expected output attributes.</p>
<p><strong><code>outputAttributes</code></strong>  : A set of output attributes separated by commas as string. Each attribute is denoted as <code>&lt;name&gt;&lt;space&gt;&lt;type&gt;</code>. e.g.,<code> 'output1 string, output2 long'</code></p></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>Output parameters are generated based on the <code>outputAttributes</code> provided.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>               evalSource('/home/user/test/script1.R', 'totalItems int, totalTemp double', items, temp)</code>, where the data type of <code>items</code> is <code>int</code> and that of <code>temp</code> is <code>double</code> returns <code>[ totalItems, totalTemp ]</code> where the data type of <code>totalTemp</code> is <code>int</code> and that of <code>totalTemp</code> is double.</p>
<div class="code panel pdl" style="border-width: 1px;">
<div class="codeContent panelContent pdl">
<div class="sourceCode" id="cb1" data-syntaxhighlighter-params="brush: java; gutter: false; theme: Confluence" data-theme="Confluence" style="brush: java; gutter: false; theme: Confluence"><pre class="sourceCode java"><code class="sourceCode java"><a class="sourceLine" id="cb1-1" title="1"><span class="at">@info</span>(name = &#39;query1&#39;) </a>
<a class="sourceLine" id="cb1-2" title="2">from dataIn#window.<span class="fu">lengthBatch</span>(<span class="dv">2</span>)#r:<span class="fu">evalSource</span>(&#39;/home/user/test/script1.<span class="fu">R</span>&#39;, &#39;totalItems <span class="dt">int</span>, totalTemp double&#39;, items, temp)</a>
<a class="sourceLine" id="cb1-3" title="3">select *</a>
<a class="sourceLine" id="cb1-4" title="4">insert into dataOut;</a></code></pre></div>
</div>
</div></td>
</tr>
</tbody>
</table>
