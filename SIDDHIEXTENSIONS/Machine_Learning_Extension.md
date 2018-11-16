# Machine Learning Extension

This extension provides Siddhi the capability to make predictions based
on Machine Learning models. Supported functions of the ML extension are
as follows.

-   [Predict function](#MachineLearningExtension-Predictfunction)

### **Predict function**

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;double|float|long|int|string|boolean&gt; ml:predict(&lt;string&gt; pathToMLModel, &lt;string&gt; dataType)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Stream Processor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><p>Returns an output event with the additional attribute that has the response variable name of the model, set with the predicted value, using the feature values extracted from the input event.</p>
<p>This function uses the following input parameters.</p>
<ul>
<li><strong><code>pathToMLModel</code></strong>: The file path or the registry path to the location of the ML model. If the model storage location is <a href="http://docs.wso2.com/governance-registry">registry</a>, the value of this parameter should have <code>registry</code> as the prefix.</li>
<li><strong><code>dataType</code></strong>: The data type of the predicted value (<code>double</code>, <code>float</code>, <code>long</code>, <code>integer/int</code>, <code>string</code>, <code>boolean</code>/<code>bool</code>).</li>
</ul></td>
</tr>
<tr class="even">
<td>Example</td>
<td><p><code> predict(‘registry:/_system/governance/mlmodels/indian-diabetes-model’)</code></p></td>
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
<td><code>&lt;double|float|long|int|string|boolean&gt; ml:predict(&lt;string&gt; pathToMLModel, &lt;string&gt; dataType, &lt;double&gt; input)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Stream Processor</td>
</tr>
<tr class="odd">
<td>Description</td>
<td><p>Returns an output event with the additional attribute that has the response variable name of the model, set with the predicted value, using the feature values extracted from the input event.</p>
<p>This function uses the following input parameters.</p>
<ul>
<li><strong><code>pathToMLModel</code></strong>: The file path or the registry path to the location of the ML model. If the model storage location is <a href="http://docs.wso2.com/governance-registry">registry</a>, the value of this parameter should have <code>registry</code> as the prefix.</li>
<li><strong><code>dataType</code></strong>: The data type of the predicted value (<code>double</code>, <code>float</code>, <code>long</code>, <code>integer/int</code>, <code>string</code>, <code>boolean</code>/<code>bool</code>).</li>
<li><strong><code>input</code></strong>: An attribute of the input stream that is sent to the ML model as a value to based on which the prediction is made. The <code>predict</code> function does not accept any constant values as input parameters. You can have multiple input parameters.</li>
</ul></td>
</tr>
<tr class="even">
<td>Example</td>
<td><code>predict(‘registry:/_system/governance/mlmodels/indian-diabetes-model’, NumPregnancies, TSFT, DPF, BMI, DBP, PG2, Age, SI2)</code></td>
</tr>
</tbody>
</table>
