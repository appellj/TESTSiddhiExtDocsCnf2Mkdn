# PMML Based Predictive Analytics Extension

This extension adds PMML based predictive analytic model compliance to
Siddhi. It allows you to make predictions based on a predictive analytic
model. Supported functions of the PMML extension are as follows.

-   [Predict
    function](#PMMLBasedPredictiveAnalyticsExtension-Predictfunction)

### Predict function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt; double | float|long|int|string|boolean &gt; pmml:predict(&lt;string&gt; pathToPmmlFile)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Stream Processor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><p>Processes the input stream attributes according to the defined PMML standard model and outputs the processed results together with the input stream attributes.</p>
<p>This function uses the following input parameter.</p>
<ul>
<li><strong><code>pathToPmmlFile</code></strong>: The path to the PMML model file.</li>
</ul>
<p>The function returns the outputs defined in the output fields. The number of outputs can vary.</p></td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code>predict('&lt;CEP HOME&gt;/samples/artifacts/0301/decision-tree.pmml')</code></p>
<p>This model is implemented to detect network intruders. The input event stream is processed by the execution plan that uses the pmml predictive model to detect whether a particular user is an intruder to the network or not. The output stream contains the processed query results that include the predicted responses together with the feature values extracted from the input event stream.</p></td>
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
<td><code>&lt; double | float|long|int|string|boolean &gt; pmml:predict(&lt;string&gt; pathToPmmlFile,  &lt;double|float|long|int|string|boolean&gt; input )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Stream Processor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><p>Processes the input stream attributes according to the defined PMML standards model and outputs the processed results.</p>
<p>This function uses the following input parameters.</p>
<ul>
<li><strong><code>pathToPmmlFile</code></strong>: The path to the PMML model file.</li>
<li><strong><code>input</code></strong>: An attribute of the input stream that is sent to the PMML standard model as a value to based on which the prediction is made. The <code>predict</code> function does not accept any constant values as input parameters. You can have multiple input parameters according to the input stream definition.</li>
</ul>
<p>This function returns the processed outputs defined in the query. The number of outputs can vary depending on the query definition.</p></td>
</tr>
<tr class="even">
<td>Examples</td>
<td><p><code>predict('&lt;CEP HOME&gt;/samples/artifacts/0301/decision-tree.pmml', root_shell, su_attempted, num_root, num_file_creations, num_shells, num_access_files, num_outbound_cmds, is_host_login, is_guest_login , count, srv_count, serror_rate, srv_serror_rate)</code></p>
<p>This model is implemented to detect network intruders. The input event stream is processed by the execution plan that uses the pmml predictive model to detect whether a particular user is an intruder to the network or not. The output stream contains the processed query results that include the predicted responses.</p></td>
</tr>
</tbody>
</table>
