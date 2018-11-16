# Geo GPL Extension

This extension provides geo data related functionality such as checking
whether a given geo coordinate is within a predefined geo-fence, etc.
Following are the functions of the Geo extension.

-   [Intersects function](#GeoGPLExtension-Intersectsfunction)
-   [Within function](#GeoGPLExtension-Withinfunction)
-   [Within Distance function](#GeoGPLExtension-WithinDistancefunction)
-   [Crosses function](#GeoGPLExtension-Crossesfunction)
-   [Stationary function](#GeoGPLExtension-Stationaryfunction)
-   [Proximity function](#GeoGPLExtension-Proximityfunction)

### **Intersects function**

|                |                                                                                                                                                                                                                                                                    |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> geo:intersects (<string> geoJSONGeometry , <string> geoJSONGeometryFence )`                                                                                                                                                                                |
| Extension Type | Function                                                                                                                                                                                                                                                           |
| Description    | Returns `true` if the  **`geoJSONGeometry`**  incoming event intersects the given string (i.e., **`geoJSONGeometryFence`** ). Returns `false` otherwise.                                                                                                           |
| Example        | `intersects( {'type':'Polygon','coordinates':[[[0.5, 0.5],[0.5, 1.5],[1.5, 1.5],[1.5, 0.5],[0.5, 0.5]]]} , {'type':'Polygon','coordinates':[[[0, 0],[0, 1],[1, 1],[1, 0],[0, 0]]]} ),` returns `true` because `geoJSONGeometry` intersects `geoJSONGeometryFence`. |

|                |                                                                                                                                                                                                                       |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> geo:           intersects (<double> longitude , <double> latitude , <string> geoJSONGeometryFence )`                                                                                                          |
| Extension Type | Function                                                                                                                                                                                                              |
| Description    | Returns `true` if the location specified in terms of longitude and latitude intersects the given  **`geoJSONGeometryFence`** . Returns `false` otherwise.                                                             |
| Example        | `intersects(0.5. 0.5 , {'type':'Polygon','coordinates':[[[0, 0],[0, 1],[1, 1],[1, 0],[0, 0]]]}),` returns `true` because the location specified in terms of longitude and latitude intersects `geoJSONGeometryFence`. |

**  
**

### **Within function**

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;bool&gt; geo:           within (&lt;double&gt; longitude , &lt;double&gt; latitude, &lt;string&gt; geoJSONGeometryFence )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns <code>true</code> if the location specified in terms of longitude and latitude is within the  <strong><code>geoJSONGeometryFence</code></strong> .</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>within(0.5, 0.5, {'type':'Polygon','coordinates':[[[0,0],[0,2],[1,2],[1,0],[0,0]]]} )</code> returns <code>true</code>.</li>
<li><code>within(2, 2, {'type':'Polygon','coordinates':[[[0,0],[0,2],[1,2],[1,0],[0,0]]]} )</code> returns <code>false</code>.</li>
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
<td><code>&lt;bool&gt; geo:           within (&lt;string&gt; geoJSONGeometry , &lt;string&gt; geoJSONGeometryFence  )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns true if the  <strong><code>geoJSONGeometry</code></strong>  is within the  <strong><code>geoJSONGeometryFence</code></strong> . Returns <code>false</code> otherwise.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><ul>
<li><code>within( {'type': 'Circle', 'radius': 110575, 'coordinates':[1.5, 1.5]} , {'type':'Polygon','coordinates':[[[0,0],[0,4],[3,4],[3,0],[0,0]]]} )</code> returns <code>true</code>.</li>
<li><code>within( {'type': 'Circle', 'radius': 110575, 'coordinates':[0.5, 1.5]} , {'type':'Polygon','coordinates':[[[0,0],[0,4],[3,4],[3,0],[0,0]]]} )</code> returns <code>false</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

**  
**

### **Within Distance function**

|                |                                                                                                                                                                                                                                                                  |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> geo:           withindistance (<double> longitude , <double> latitude, <string> geoJSONGeometryFence )`                                                                                                                                                  |
| Extension Type | Function                                                                                                                                                                                                                                                         |
| Description    | Returns `true` if the location specified in terms of longitude and latitude is within distance of the  **`geoJSONGeometryFence`** . Returns `false` otherwise.                                                                                                   |
| Example        | `withindistance( 0.5 , 0.5, {'type':'Polygon','coordinates':[[[0, 0],[0, 1],[1, 1],[1, 0],[0, 0]]]}, 110574.61087757687)` returns `true` because the location specified in terms of longitude and latitude is within the distance of the `geoJSONGeometryFence`. |

|                |                                                                                                                                                                                                                                                                                                         |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> geo:           withindistance (<string> geoJSONGeometry , <string> geoJSONGeometryFence , <double> distance )`                                                                                                                                                                                  |
| Extension Type | Function                                                                                                                                                                                                                                                                                                |
| Description    | Returns `true` if the area given by  **`geoJSONGeometry`**  is within distance of the  **`geoJSONGeometryFence`** .                                                                                                                                                                                     |
| Example        | `withindistance( {'type':'Polygon','coordinates':[[[0.5, 0.5],[0.5, 1.5],[1.5, 1.5],[1.5, 0.5],[0.5, 0.5]]]} , {'type':'Polygon','coordinates':[[[0, 0],[0, 1],[1, 1],[1, 0],[0, 0]]]}, 110574.61087757687)` returns `true` because `geoJSONGeometry` is within the distance of `geoJSONGeometryFence`. |

**  
**

### **Crosses function**

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;bool&gt; geo:           crosses (&lt;string&gt; id , &lt;double&gt; longitude, &lt;double&gt; latitude , &lt;string&gt; geoJSONGeometryFence )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns <code>true</code> when the  the specified object of which the location is specified  in terms of  <strong><code>longitude</code></strong>   and  <strong><code>latitude</code></strong>  crosses the geographic location specified in  <strong><code>geoJSONGeometryFence</code></strong> . Returns <code>false</code> when the object crosses out of the location specified in  <strong><code>geoJSONGeometryFence</code></strong> .</td>
</tr>
<tr class="even">
<td>Example</td>
<td><ul>
<li><code>crosses(km-4354, -0.5, 0.5, {'type':'Polygon','coordinates':[[[0, 0],[2, 0],[2, 1],[0, 1],[0, 0]]]} )</code> returns <code>true</code>.</li>
<li><code>km-4354, 1.5, 0.5, {'type':'Polygon','coordinates':[[[0, 0],[2, 0],[2, 1],[0, 1],[0, 0]]]} )</code> returns <code>true</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

|                |                                                                                                                                                                                                                          |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> geo:           crosses (<string> id , <string> geoJSONGeometry , <string> geoJSONGeometryFence )`                                                                                                                |
| Extension Type | StreamProcessor                                                                                                                                                                                                          |
| Description    | Returns true when the object (i.e.  **`geoJSONGeometry`** ) crosses the specified geographic location (i.e.  **`geoJSONGeometryFence`** ). Returns `false` when the object crosses out of **` geoJSONGeometryFence`** .  |

 

### Stationary function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;bool&gt; geo:           stationary (&lt;string&gt; id , &lt;double&gt; longitude, &lt;double&gt; latitude , &lt;string&gt; geoJSONGeometryFence , &lt;double&gt; radius )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns <code>true</code> when the object (defined in terms of   <strong><code>longitude</code></strong>   and  <strong><code>latitude</code></strong> ) becomes stationary within the specified  <strong><code>radius</code></strong> . Returns <code>false</code> when the object moves out of the specified <strong>radius</strong>.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><ul>
<li><code>stationary(km-4354,0,0, 110574.61087757687)</code> returns <code>true</code>.</li>
<li><code>stationary(km-4354,1,1, 110574.61087757687) </code>returns <code>               true</code>.</li>
<li><code>stationary(km-4354,1,1.5, 110574.61087757687)</code> returns <code>true</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

|                |                                                                                                                                                                                             |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> geo:           stationary (<string> id , <string> geoJSONGeometry , <string> geoJSONGeometryFence , <double>  radius )`                                                             |
| Extension Type | StreamProcessor                                                                                                                                                                             |
| Description    | Returns `true` when the object (i.e.  **`geoJSONGeometry`** ) becomes stationary within the specified  **`radius`** `. `Returns `false `when the objects moves out of the specified radius. |

### Proximity function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;bool,string&gt; geo:proximity (&lt;string&gt; id , &lt;double&gt; longitude, &lt;double&gt; latitude , &lt;string&gt; geoJSONGeometryFence , &lt;double&gt; radius )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns <code>true</code> when two objects (specified in terms of <code>           longitude         </code> and <code>           latitude) </code>are within the specified  <strong><code>radius</code></strong>  to another object. Returns <code>false</code> when the specified object moves out of the specified  <strong><code>radius</code></strong> . The <code>proximityWith</code> optional attribute indicates the ID of the object that the object specified is in close proximity with. <code>proximityID</code> is a unique ID for the two objects in close proximity.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><p>The following return <code>true</code> with <code>             id 3</code>.</p>
<ul>
<li><code>proximity(1, 0, 0, 110574.61087757687)</code></li>
<li><code>proximity(2, 1, 1, 110574.61087757687)</code></li>
<li><code>proximity(3, 2, 2, 110574.61087757687)</code></li>
<li><code>proximity(1, 1.5, 1.5, 110574.61087757687)</code></li>
</ul></td>
</tr>
</tbody>
</table>

|                |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> proximity (<string> id , <string> geoJSONGeometry , <string> geoJSONGeometryFence , <double>  radius )`                                                                                                                                                                                                                                                                                                                                                                 |
| Extension Type | StreamProcessor                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Description    | Returns `true` when an object (i.e.  **`geoJSONGeometry`** ) is within the specified  **`radius`**  from another object. Returns `false` when one or both objects move away from each other and are no longer within the specified `           radiu         `s of each other. The `proximityWith` optional attribute indicates the ID of the object that the object specified is in close proximity with. `proximityID` is a unique ID for the two objects in close proximity. |
