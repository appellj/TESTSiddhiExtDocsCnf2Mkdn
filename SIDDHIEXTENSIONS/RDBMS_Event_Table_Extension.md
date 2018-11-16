# RDBMS Event Table Extension

The RDBMS event table has been tested with the following databases: 

-   MySQL
-    H2
-    Oracle

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
<td>An event table can be backed with an RDBMS event store using the <code>From</code> annotation. This annotation also assigns the data source or the connection instructions to the event table. The RDBMS table name can be different to the event table name defined in Siddhi, and Siddhi always refers to the defined event table name. However the defined event table name cannot be same as an already existing stream name because the Siddhi Query Language considers both to be the same syntactically. </td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><ul>
<li><strong><code>eventable type</code></strong>: The constant value that defines the type of the event table. For Hazlecast event table, use <strong><code>rdbms</code></strong>.</li>
<li><strong><code>property name</code></strong>: The rdbms data source connection configuration properties. The available properties are as follows.
<ul>
<li><strong><code>datasource.name</code></strong>: The datasource name is injected to the Siddhi engine by the CEP/DAS. This is not required To configure datasources in CEP/DAS see <a href="https://docs.wso2.com/display/ADMIN44x/Managing+Datasources">Managing Datasources in the WSO2 Administration Guide</a>.</li>
<li><strong><code>table.name</code></strong>: The reference table name defined in the datasource.</li>
<li><strong><code>jdbc.url</code></strong>: The jdbc url for the databases that are not registered as datasources.</li>
<li><strong><code>driver.name</code></strong>: The jdbc driver name for the databases that are not registered as datasources.</li>
<li><strong><code>username</code></strong>: The username for the databases that are not registered as datasources.</li>
<li><strong><code>password</code></strong>: The password for the databases that are not registered as datasources.</li>
<li><strong><code>cache</code></strong>: Several caches can be used with RDMBS backed event tables in order to reduce I/O operations and improve their performance. Currently all cache implementations provides size-based algorithms. The supported cache implementations are as follows.
<ul>
<li><strong><code>Basic</code></strong>: Events are cached in a FIFO manner where the oldest event is dropped when the cache is full.</li>
<li>LRU (Least Recently Used): The least recently used event is dropped when the cache is full.</li>
<li>LFU (Least Frequently Used): The least frequently used event is dropped when the cache is full.</li>
</ul></li>
<li><strong><code>cache.size</code></strong>: The size of the cache. If the element is not assigned, 4096 is assigned as the cache size by default.</li>
</ul></li>
<li><strong><code>bloom.filters</code></strong>: This property enables/disables the bloom filters. A Bloom Filter is an algorithm or an approach that can be used to perform quick searches. If you apply a Bloom Filter to a data set and carry out an isAvailable check on that specific Bloom Filter instance, an accurate answer is returned if the search item is not available. This allows the quick improvement of updates, joins and isAvailable checks.</li>
<li><strong><code>property value</code></strong>: This defines values for all the properties.</li>
<li><strong><code>table name</code></strong>: This defines the name of the table.</li>
<li><strong><code>attribute name</code></strong>: This defines the name of the table column.</li>
<li><strong><code>attribute type</code></strong>: This defines the type of the table column.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Return</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>Example</td>
<td><ul>
<li><p>The following creates an event table named <code>RoomTypeTable</code> with two attributes named <code>roomNo</code> (an INT attribute) and <code>type</code> (a STRING attribute), backed by a MySQL table named <code>RoomTable</code> from the <code>cepdb</code> database located at <code>localhost:3306</code> with <code>root</code> as both the username and password.</p>
<div class="code panel pdl" style="border-width: 1px;">
<div class="codeContent panelContent pdl">
<div class="sourceCode" id="cb1" data-syntaxhighlighter-params="brush: sql; gutter: true; theme: Confluence" data-theme="Confluence" style="brush: sql; gutter: true; theme: Confluence"><pre class="sourceCode sql"><code class="sourceCode sql"><a class="sourceLine" id="cb1-1" title="1"><span class="ot">@From(eventtable=&#39;rdbms&#39;, datasource.name=&#39;AnalyticsDataSource&#39;, table.name=&#39;RoomTable&#39;)</span></a>
<a class="sourceLine" id="cb1-2" title="2">define <span class="kw">table</span> RoomTypeTable (roomNo <span class="dt">int</span>, <span class="kw">type</span> string);</a></code></pre></div>
</div>
</div></li>
<li><p>The following creates an event table named RoomTypeTable with two attributes named roomNo (an INT attribute) and type (a STRING attribute), backed by an RDBMS table using he LRU caching algorithm for caching 3000 events. </p>
<div class="code panel pdl" style="border-width: 1px;">
<div class="codeContent panelContent pdl">
<div class="sourceCode" id="cb2" data-syntaxhighlighter-params="brush: sql; gutter: false; theme: Confluence" data-theme="Confluence" style="brush: sql; gutter: false; theme: Confluence"><pre class="sourceCode sql"><code class="sourceCode sql"><a class="sourceLine" id="cb2-1" title="1"><span class="ot">@From(eventtable=&#39;rdbms&#39;, datasource.name=&#39;AnalyticsDataSource&#39;, table.name=&#39;RoomTable&#39;, cache=&#39;LRU&#39;, cache.size=&#39;3000&#39;)</span></a>
<a class="sourceLine" id="cb2-2" title="2">define <span class="kw">table</span> RoomTypeTable (roomNo <span class="dt">int</span>, <span class="kw">type</span> string);</a></code></pre></div>
</div>
</div></li>
<li><p>The following example shows how to include Bloom Filters in an event table update query.</p>
<div class="code panel pdl" style="border-width: 1px;">
<div class="codeContent panelContent pdl">
<div class="sourceCode" id="cb3" data-syntaxhighlighter-params="brush: sql; gutter: false; theme: Confluence" data-theme="Confluence" style="brush: sql; gutter: false; theme: Confluence"><pre class="sourceCode sql"><code class="sourceCode sql"><a class="sourceLine" id="cb3-1" title="1">define stream StockStream (symbol string, price <span class="dt">float</span>, volume <span class="dt">long</span>);</a>
<a class="sourceLine" id="cb3-2" title="2">define stream CheckStockStream (symbol string, volume <span class="dt">long</span>);</a>
<a class="sourceLine" id="cb3-3" title="3"><span class="ot">@from(eventtable = &#39;rdbms&#39; ,datasource.name = &#39;cepDB&#39; , table.name = &#39;stockInfo&#39; , bloom.filters = &#39;enable&#39;)</span></a>
<a class="sourceLine" id="cb3-4" title="4">define <span class="kw">table</span> StockTable (symbol string, price <span class="dt">float</span>, volume <span class="dt">long</span>);</a>
<a class="sourceLine" id="cb3-5" title="5">  </a>
<a class="sourceLine" id="cb3-6" title="6"><span class="ot">@info(name = &#39;query1&#39;)</span></a>
<a class="sourceLine" id="cb3-7" title="7"><span class="kw">from</span> StockStream</a>
<a class="sourceLine" id="cb3-8" title="8"><span class="kw">insert</span> <span class="kw">into</span> StockTable ;</a>
<a class="sourceLine" id="cb3-9" title="9">  </a>
<a class="sourceLine" id="cb3-10" title="10"><span class="ot">@info(name = &#39;query2&#39;)</span></a>
<a class="sourceLine" id="cb3-11" title="11"><span class="kw">from</span> CheckStockStream[(StockTable.symbol<span class="op">==</span>symbol) <span class="kw">in</span> StockTable]</a>
<a class="sourceLine" id="cb3-12" title="12"><span class="kw">insert</span> <span class="kw">into</span> OutStream;</a></code></pre></div>
</div>
</div>
<p> </p>
<div>

</div></li>
</ul></td>
</tr>
</tbody>
</table>

For more information about In-memory event tables, see [Sample 0106 -
Using in-memory event
tables](http://docs.wso2.com/complex-event-processor/Sample%200107%20-%20Using%20RDBMS%20event%20tables)[.](https://docs.wso2.com/display/CEP400/Sample+0106+-+Using+in-memory+event+tables)

For more information about RDBMS event tables, see [Sample 0107 - Using
RDBMS event
tables](http://docs.wso2.com/complex-event-processor/Sample%200107%20-%20Using%20RDBMS%20event%20tables)[.](https://docs.wso2.com/display/CEP400/Sample+0107+-+Using+RDBMS+event+tables)
