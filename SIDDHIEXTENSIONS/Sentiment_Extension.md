# Sentiment Extension

**Sentiment Analysis** refers to the process of determining whether a
piece of writing is positive, negative or neutral. It is also known as
opinion mining, deriving the opinion or deriving the attitude of a given
text.

-   [Sentiment function](#SentimentExtension-Sentimentfunction)

### Sentiment function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;int&gt; sentiment:getRate(&lt;string&gt; text)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>The <strong><code>sentiment:getRate</code></strong> is applied to some text in string format to obtain a rating as to whether it is positive, negative or neutral.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td> </td>
</tr>
<tr class="odd">
<td>Example</td>
<td><p><code>sentiment:getRate(“&quot;What is wrong with these people&quot;)</code> returns <code>-2</code>.</p>
<p>e.g., An event stream is defined as follows.</p>
<p><code>define stream inputStream (text string);</code></p>
<p>The sentiment extension can be used as follows.</p>
<p><code>from inputStream </code></p>
<p><code>select sentiment:getRate(text) as isRate </code></p>
<p><code>insert into outputStream;</code></p>
<div>
<div>
<p>Here, the input is the input sentence in <code>STRING</code> format. The output is an integer determining the positive or negative aspect of the sentence.</p>
</div>
</div></td>
</tr>
</tbody>
</table>
