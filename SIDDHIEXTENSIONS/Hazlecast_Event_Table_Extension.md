# Hazlecast Event Table Extension

**Connection instructions that can be used with the From annotation:** 

cluster.name : Hazelcast cluster name \[Optional\]
 (i.e cluster.name='cluster\_a').

cluster.password :  Hazelcast cluster
password \[Optional\] (i.e cluster.password='pass@cluster\_a').

cluster.addresses :  Hazelcast cluster addresses as a comma separated
string \[Optional\] (i.e
cluster.addresses='192.168.1.1:5700,192.168.1.2.5700').

 

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>@from(eventtable = &lt;eventtable type&gt;, [&lt;property name&gt; =  &lt;property value&gt;]*)</code></p>
<p><code>[@IndexBy(&lt;attribute name&gt;)]?</code></p>
<code>define table &lt;table name&gt; ([&lt;attribute name&gt; &lt;attribute type&gt;]+);</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>EventTable</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><p>Hazelcast event tables support persisting event data in a distributed manner using Hazelcast in-memory data grids. This functionality is enabled via the <code>From</code> annotation. This annotation also assigns the instructions for the Hazelcast cluster to the event table.</p>
<p>An event table can be indexed for fast event access using the<code> IndexBy</code> annotation. With <code>IndexBy</code>, only one attribute can be indexed. Once the indexing is done, events are held using a map data structure. Therefore if multiple events are inserted into an event table with the same index value, only the event that was inserted last remains in the table.</p></td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>eventtable type</code></strong>: This is a constant value that defines the type of the event table. For Hazelcast event tables, use <code>hazelcast</code>.</li>
<li><strong><code>property name</code></strong>: The hazelcast cluster connection configuration properties. Available properties are as follows.
<ul>
<li><strong><code>cluster.name</code></strong>: The name of the Hazelcast cluster.</li>
<li><strong><code>cluster.password</code></strong>: The password of the Hazelcast cluster.</li>
<li><strong><code>cluster.addresses</code></strong>: The Hazelcast cluster addresses as a comma separated string.</li>
</ul></li>
<li><strong><code>property value</code></strong>: Defines the connection values for each property.</li>
<li><strong><code>table name</code></strong>: Defines the name of the table.</li>
<li><strong><code>attribute name</code></strong>: Defines the table column name.</li>
<li><strong><code>attribute type</code></strong>: Defines the table column type.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><p>The following creates an event table named <code>RoomTypeTable</code> with attributes named <code>roomNo</code> (an INT attribute) and <code>type</code> (a STRING attribute), backed by a new Hazelcast Instance.</p>
<div class="code panel pdl" style="border-width: 1px;">
<div class="codeContent panelContent pdl">
<div class="sourceCode" id="cb1" data-syntaxhighlighter-params="brush: sql; gutter: false; theme: Confluence" data-theme="Confluence" style="brush: sql; gutter: false; theme: Confluence"><pre class="sourceCode sql"><code class="sourceCode sql"><a class="sourceLine" id="cb1-1" title="1"><span class="ot">@from(eventtable = &#39;hazelcast&#39;)</span></a>
<a class="sourceLine" id="cb1-2" title="2">define <span class="kw">table</span> RoomTypeTable(roomNo <span class="dt">int</span>, <span class="kw">type</span> string);</a></code></pre></div>
</div>
</div></li>
<li><p>The following creates an event table named <code>RoomTypeTable</code> with attributes named <code>roomNo</code> (an INT attribute) and <code>type</code> (a STRING attribute), backed by a new Hazelcast Instance in a new Hazelcast Cluster.</p>
<div class="code panel pdl" style="border-width: 1px;">
<div class="codeContent panelContent pdl">
<div class="sourceCode" id="cb2" data-syntaxhighlighter-params="brush: sql; gutter: false; theme: Confluence" data-theme="Confluence" style="brush: sql; gutter: false; theme: Confluence"><pre class="sourceCode sql"><code class="sourceCode sql"><a class="sourceLine" id="cb2-1" title="1"><span class="ot">@from(eventtable = &#39;hazelcast&#39;, cluster.name = &#39;cluster_a&#39;, cluster.password = &#39;pass@cluster_a&#39;)</span></a>
<a class="sourceLine" id="cb2-2" title="2">define <span class="kw">table</span> RoomTypeTable(roomNo <span class="dt">int</span>, <span class="kw">type</span> string);</a></code></pre></div>
</div>
</div></li>
<li><p>The following creates an event table named <code>RoomTypeTable</code> with attributes named <code>roomNo</code> (an INT attribute) and <code>type</code> (a STRING attribute), backed by an existing Hazelcast Instance in an existing Hazelcast cluster.</p>
<div class="code panel pdl" style="border-width: 1px;">
<div class="codeContent panelContent pdl">
<div class="sourceCode" id="cb3" data-syntaxhighlighter-params="brush: sql; gutter: false; theme: Confluence" data-theme="Confluence" style="brush: sql; gutter: false; theme: Confluence"><pre class="sourceCode sql"><code class="sourceCode sql"><a class="sourceLine" id="cb3-1" title="1"><span class="ot">@from(eventtable = &#39;hazelcast&#39;, cluster.name = &#39;cluster_a&#39;, cluster.password = &#39;pass@cluster_a&#39;, cluster.addresses=&#39;192.168.1.1:5700,192.168.1.2.5700&#39;)</span></a>
<a class="sourceLine" id="cb3-2" title="2">define <span class="kw">table</span> RoomTypeTable(roomNo <span class="dt">int</span>, <span class="kw">type</span> string);</a></code></pre></div>
</div>
</div>
<p> </p></li>
</ul></td>
</tr>
</tbody>
</table>
