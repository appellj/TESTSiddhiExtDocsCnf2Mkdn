# Geo Extension

This extension provides geo data related functionality such as checking
whether a given geo coordinate is within a predefined geo-fence, etc.
Following are the functions of the Geo extension.

-   [Geo Coordinates function](#GeoExtension-GeoCoordinatesfunction)
-   [Reverse Geocode Stream
    Function](#GeoExtension-ReverseGeocodeStreamFunction)

### Geo Coordinates function

<table>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;double, double, string&gt; geocode ( location          </code> )</td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>StreamProcessor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Transforms a location to its geo-coordinates ( <strong><code> longitude</code></strong>  and  <strong><code>latitude</code></strong>  ) and formatted address.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>geocode(duplication rd)</code> returns the following data with adherring latitude, longitude, and <code>formattedAddress</code> attribute names respectively.<br />
<code>6.8995244d, 79.8556202d, &quot;R A De Mel Mawatha, Colombo, Sri Lanka&quot; </code></td>
</tr>
</tbody>
</table>

### Reverse Geocode Stream Function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;object&gt;geo:reversegeocode(&lt;int,long,double,float&gt;latitude, &lt;int,long,double,float&gt;longitude)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Stream Function Processor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Transforms latitude and longitude coordinates into precise address information.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td><p><strong><code>latitude</code></strong>: The input location specified in terms of latitude.</p>
<strong><code>longitude</code></strong>: The input location specified in terms of longitude.</td>
</tr>
<tr class="odd">
<td>Return</td>
<td><p>The output object contains an array of string properties including the <code>streetNumber</code>, <code>neighborhood</code>, <code>route</code>, <code>administrativeAreaLevelTwo</code>, <code>administrativeAreaLevelOne</code>, <code>country</code>, <code>countryCode</code>, <code>postalCode</code> and <code>formattedAddress</code> in the given order.</p>
However, all this information is not available for all the geo coordinates. For example, if the latitude and longitude represent a place in a forest, only the high level information such as the country is returned. <code>N/A</code> is returned for properties for which values cannot be obtained.</td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>geo:reversegeocode(40.715229, -73.8564082)</code> returns <code>{&quot;67-53&quot;, &quot;Flushing&quot;, &quot;Loubet Street&quot;, &quot;Queens County&quot;, &quot;New York&quot;, &quot;United States&quot;, &quot;US&quot;, &quot;11375&quot;, &quot;67-53 Loubet St, Flushing, NY 11375, USA&quot;}</code></td>
</tr>
</tbody>
</table>
