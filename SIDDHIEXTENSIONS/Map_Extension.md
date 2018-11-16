# Map Extension

This extension provides the capability to send a map object inside
Siddhi stream definitions and use it inside queries. The following are
the functions of the `map` extension.

-   [Create function](#MapExtension-Createfunction)
-   [Get function](#MapExtension-Getfunction)
-   [Is Map function](#MapExtension-IsMapfunction)
-   [Put function](#MapExtension-Putfunction)
-   [Remove function](#MapExtension-Removefunction)
-   [Create from JSON function](#MapExtension-CreatefromJSONfunction)
-   [Create from XML function](#MapExtension-CreatefromXMLfunction)
-   [To JSON function](#MapExtension-ToJSONfunction)
-   [To XML function](#MapExtension-ToXMLfunction)

### Create function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>&lt;Object&gt; map:create()           </code></p>
<p>or</p>
<p><code>&lt;Object&gt; map:create(&lt;Object&gt; key1, &lt;Object&gt; value1,&lt;Object&gt; key2, &lt;Object&gt; value2,...&lt;Object&gt; keyN, &lt;Object&gt; valueN)</code></p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns the created map object.</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>create()</code> returns an empty map.</li>
<li><code>create(1 , ”one” ,  2 , ”two” , 3 , ”three”)</code> returns a map with keys <code>1, 2, 3</code> and corresponding values <code>&quot;one&quot;, &quot;two&quot;, &quot;three&quot;</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

 

### Get function

|                |                                                                                                 |
|----------------|-------------------------------------------------------------------------------------------------|
| Syntax         | `<Object> map:get(<Map> map, <Object> key)`                                                     |
| Extension Type | Function                                                                                        |
| Description    | Returns the value object from the map that is related to the given key.                         |
| Example        | `get(company,1)` returns the value that is related to the key `1` from the map named `company`. |

 

### Is Map function

|                |                                                                                                                             |
|----------------|-----------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> map:isMap(<Object> object)`                                                                                         |
| Extension Type | Function                                                                                                                    |
| Description    | Returns `true` if the object is a map or `false` otherwise.                                                                 |
| Example        | `isMap(students)` returns `true` if the students object is a map. It returns `false` if the `students` object is not a map. |

 

### Put function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>&lt;Object&gt; map:put(&lt;Object&gt; map, &lt;Object&gt; key,&lt;Object&gt; value)</code></p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns the updated map after adding the given key-value pair.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>put(students , 1234 , ”sam”)</code> returns the updated map named <code>students</code> after adding the object <code>&quot;sam&quot;</code> with key <code>1234</code>.</td>
</tr>
</tbody>
</table>

 

### Remove function

|                |                                                                                                              |
|----------------|--------------------------------------------------------------------------------------------------------------|
| Syntax         | `<Object> map:remove(<Object> map, <Object> key)`                                                            |
| Extension Type | Function                                                                                                     |
| Description    | Returns the updated map after removing the element with key.                                                 |
| Example        | `remove(students , 1234)` returns the updated map `students` after removing the element with the key `1234`. |

### Create from JSON function

|                |                                                                                                                                                                                                |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<Object> map:createFromJSON(<string> JSONstring)`                                                                                                                                             |
| Extension Type | Function                                                                                                                                                                                       |
| Description    | Returns the map created with the key values pairs given in the `JSONstring`.                                                                                                                   |
| Example        | `createFromJSON(“{‘symbol' : 'IBM' , 'price' : 200, 'volume' : 100}”)` returns a map with the keys "`symbol"`, `"price", "volume"`, and with the values `"IBM"`, `200` and `100` respectively. |

 

### Create from XML function

|                |                                                                                                                                                                                                                                        |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<Object> map:createFromXML(<string> XMLstring)`                                                                                                                                                                                       |
| Extension Type | Function                                                                                                                                                                                                                               |
| Description    | Returns the map created with the key values pairs given in the XMLstring.                                                                                                                                                              |
| Example        | `createFromXML(“<company> <symbol> wso2 </symbol> <price> <100> </price> <volume> 200 </volume> </company>”)` returns a map with the keys `"symbol"`, `"price"`, `"volume"`, and with the values `WSO2`, `100` and `200` respectively. |

 

### To JSON function

|                |                                                                                                                                                                                                           |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<String> map:toJSON(<Object> map)`                                                                                                                                                                       |
| Extension Type | Function                                                                                                                                                                                                  |
| Description    | Converts a map into a JSON object and returns the definition of that JSON object as a string.                                                                                                             |
| Example        | If `"company"` is a map with key value pairs `("symbol" : wso2)`, `("volume" : 100)`, and `("price",200)`, `toJSON(company)` returns the string `“{“symbol” : “wso2” , “volume” : 100 , “price” : 200}”`. |

 

### To XML function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><p><code>&lt;String&gt; map:toXML(&lt;Object&gt; map)</code></p>
<p>or</p>
<p><code>&lt;String&gt; map:toXML(&lt;Object&gt; map, &lt;String&gt; rootElementName)</code></p></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns the map as an XML string.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p>If<code> &quot;company&quot;</code> is a map with key value pairs <code>(“symbol” : wso2)</code>, <code>(“volume” : 100)</code>, and <code>(“price” : 200),</code></p>
<p><code>toXML(company)</code> returns the string <code>“&lt;symbol&gt;wso2&lt;/symbol&gt;&lt;volume&gt;&lt;100&gt;&lt;/volume&gt;&lt;price&gt;200&lt;/price&gt;&quot;</code>.</p>
<p><code>toXML(company, &quot;abcCompany&quot;)</code> returns the string <code>“&lt;abcCompany&gt;&lt;symbol&gt;wso2&lt;/symbol&gt;&lt;volume&gt;&lt;100&gt;&lt;/volume&gt;&lt;price&gt;200&lt;/price&gt;&lt;/abcCompany&gt;&quot;</code>.</p></td>
</tr>
</tbody>
</table>
