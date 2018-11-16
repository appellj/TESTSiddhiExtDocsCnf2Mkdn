# String Extension

This extension provides basic string handling capabilities such as
con-cat, length, convert to lowercase, replace all, etc. String
extension can be used in a query as follows. Following are the functions
of the String extension.

-   [Char At function](#StringExtension-CharAtfunction)
-   [Coalesce function](#StringExtension-Coalescefunction)
-   [Concatenation function](#StringExtension-Concatenationfunction)
-   [Contains function](#StringExtension-Containsfunction)
-   [Hexadecimal function](#StringExtension-Hexadecimalfunction)
-   [Length function](#StringExtension-Lengthfunction)
-   [Lower Case function](#StringExtension-LowerCasefunction)
-   [Regular Expression
    function](#StringExtension-RegularExpressionfunction)
-   [Repeat function](#StringExtension-Repeatfunction)
-   [Replace All function](#StringExtension-ReplaceAllfunction)
-   [Replace First function](#StringExtension-ReplaceFirstfunction)
-   [Reverse function](#StringExtension-Reversefunction)
-   [Split function](#StringExtension-Splitfunction)
-   [String Compare function](#StringExtension-StringComparefunction)
-   [Sub String function](#StringExtension-SubStringfunction)
-   [Trim function](#StringExtension-Trimfunction)
-   [Unhexadecimal function](#StringExtension-Unhexadecimalfunction)
-   [Upper Case function](#StringExtension-UpperCasefunction)

### Char At function

|                |                                                                  |
|----------------|------------------------------------------------------------------|
| Syntax         | `<string> str:charAt(<string> str, <int>  index)`                |
| Extension Type | Function                                                         |
| Description    | Returns the char value as a string value at the specified index. |
| Example        | `charAt("WSO2", 1)` returns `'S'`.                               |

 

### Coalesce function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt; int|long|float|double|string|boolean &gt; str:           coalesce (&lt; int|long|float|double|string|boolean &gt;  arg1, &lt; int|long|float|double|string|boolean &gt;   arg2 ,.., &lt; int|long|float|double|string|boolean &gt;   argN )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns the value of the first of its input parameters that is not null.</td>
</tr>
<tr class="even">
<td>Parameters</td>
<td>This functions accepts any number of parameters. The parameters can be of different types.</td>
</tr>
<tr class="odd">
<td>Return Type</td>
<td>This is the same as the type of the first input parameter that is not null.</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>coalesce(&quot;123&quot;, null, &quot;789&quot;)</code> returns <code>&quot;123&quot;</code>.</li>
<li><code>coalesce(null, &quot;BBB&quot;, &quot;CCC&quot;)</code> returns <code>&quot;BBB&quot;</code>.</li>
<li><code>coalesce(null, null, null)</code> returns <code>null</code>.  </li>
</ul></td>
</tr>
</tbody>
</table>

 

### Concatenation function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;string&gt; str:           concat   ( &lt;int|long|float|double|string|boolean &gt; arg1, &lt; int|long|float|double|string|boolean &gt;   arg2 ,.., &lt; int|long|float|double|string|boolean &gt;   argN )</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Returns a string that is the result of concatenating the given arguments:  <strong><code>arg1</code></strong> ,  <strong><code>arg2</code></strong> , ..,  <strong><code>argN</code></strong> .</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>concat(&quot;D533&quot;, &quot;8JU^&quot;, &quot;XYZ&quot;)</code> returns <code>&quot;D5338JU^XYZ&quot;</code>.</li>
<li><code>concat(&quot;AAA&quot;, null, &quot;CCC&quot;)</code> returns <code>&quot;AAACCC&quot;</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

 

### Contains function

|                |                                                                                                                                      |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<bool> str:           contains ( < string> inputSequence, <string>  searchingSequence )`                                            |
| Extension Type | Function                                                                                                                             |
| Description    | This method returns `true` if  **`inputSequence`**  contains the specified sequence of char values in the  **`searchingSequence`** . |
| Example        | `contains("21 products are produced by WSO2 currently", "WSO2")` returns `true`.                                                     |

 

### Hexadecimal function

|                |                                                             |
|----------------|-------------------------------------------------------------|
| Syntax         | `<string> str:           hex   ( < string> str)`            |
| Extension Type | Function                                                    |
| Description    | Returns a hexadecimal string representation of  **`str`** . |
| Example        | `hex("MySQL")` returns `"4d7953514c"`.                      |

 

### Length function

|                |                                                  |
|----------------|--------------------------------------------------|
| Syntax         | `<int> str:           length   ( < string> str)` |
| Extension Type | Function                                         |
| Description    | Returns the length of the string:  **`str`** .   |
| Examples       | `length("Hello World")` returns `11`.            |

 

### Lower Case function

|                |                                                                                                |
|----------------|------------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           lower   ( < string> str)`                                             |
| Extension Type | Function                                                                                       |
| Description    | Converts the capital letters in the  **`str`**  input string to the equivalent simple letters. |
| Example        | `lower("WSO2 cep ")` returns `"wso2 cep "`.                                                    |

### Regular Expression function

|                |                                                                                                                                                                                          |
|----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<boolean> str:           regexp   ( < string> str, <string> regex )`                                                                                                                    |
| Extension Type | Function                                                                                                                                                                                 |
| Description    | Returns `true` if the given string (i.e.  **`str`** `)` matches the given regular expression (i.e.  **`regex`**  ). Returns `false` if the string does not match the regular expression. |
| Example        | `regexp("WSO2 abcdh", "WSO(.*h)")` returns `true`.                                                                                                                                       |

 

### Repeat function

|                |                                                                                                            |
|----------------|------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           repeat   ( < string> str, <int>  times)`                                          |
| Extension Type | Function                                                                                                   |
| Description    | Repeats the specified string (i.e.  **`string`** ) for the specified number of times (i.e.  **`times`** ). |
| Example        | `repeat("StRing 1", 3)` returns `"StRing 1StRing 1StRing 1"`.                                              |

 

### Replace All function

|                |                                                                                                                                                                                                        |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           replaceAll   ( < string> str, <string>  regex ,  <string>  replacement)`                                                                                                      |
| Extension Type | Function                                                                                                                                                                                               |
| Description    | Replaces each substring of the given string (i.e.  **`str`** ) that matches the given regular expression (i.e.  **`regex`** ) with the string specified as the replacement (i.e. **` replacement`** ). |
| Example        | `replaceAll("hello hi hello",  'hello', 'test')` returns `"test hi test"`.                                                                                                                             |

 

### Replace First function

|                |                                                                                                                                                                                                 |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           replaceFirst (< string>  str ,  <string>  regex ,  <string>  replacement )`                                                                                            |
| Extension Type | Function                                                                                                                                                                                        |
| Description    | Replaces the first substring that matches the given regular expression (i.e. `           regex         `) with the string specified as the replacement (i.e. `           replacement         `) |
| Example        | `replaceFirst("hello WSO2 A hello",  'WSO2(.*)A', 'XXXX')` returns `"hello XXXX hello"`.                                                                                                        |

 

### Reverse function

|                |                                                      |
|----------------|------------------------------------------------------|
| Syntax         | `<string> str:           reverse   ( < string> str)` |
| Extension Type | Function                                             |
| Description    | Returns the reverse ordered string of  **`str`** .   |
| Example        | `reverse("Hello World")` returns `"dlroW olleH"`.    |

 

### Split function

|                |                                                                                                                                                                |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           split ( <string> sourceString, <string> splitCharacter, <int> returnedOutputPosition )`                                               |
| Extension Type | Function                                                                                                                                                       |
| Description    | This method splits the given  **`sourceString`**  by given  **`splitCharacter`**  and returns the string in the index given by  **`returnedOutputPosition`** . |
| Example        | `split("WSO2,ABM,NSFT", ",", 0)` returns `WSO2`.                                                                                                               |

 

### String Compare function

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td>Syntax</td>
<td><code>&lt;int&gt; str:           strcmp ( &lt; string&gt; str, &lt;string&gt;  compareTo)</code></td>
</tr>
<tr class="even">
<td>Extension Type</td>
<td>Function</td>
</tr>
<tr class="odd">
<td>Description</td>
<td>Compares  <strong><code>str</code></strong>  with  <strong><code>compareTo</code></strong>  strings lexicographically.</td>
</tr>
<tr class="even">
<td>Examples</td>
<td><ul>
<li><code>strcmp(&quot;Hello&quot;, 'Hello')</code> returns <code>0</code>.</li>
<li><code>strcmp(&quot;AbCDefghiJ KLMN&quot;, 'Hello')</code> returns <code>-7</code>.</li>
</ul></td>
</tr>
</tbody>
</table>

 

### Sub String function

|                |                                                                               |
|----------------|-------------------------------------------------------------------------------|
| Syntax         | `<string> str:           substr   ( < string> sourceText, <int> beginIndex )` |
| Extension Type | Function                                                                      |
| Description    | Returns a ne string that is a substring of `           sourceText.`           |
| Example        | `substr("AbCDefghiJ KLMN", 4)` returns `"efghiJ KLMN"`.                       |

|                |                                                                                              |
|----------------|----------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           substr   ( < string> sourceText, <int> beginIndex,  <int> length )` |
| Extension Type | Function                                                                                     |
| Description    |  Returns a new string that is a substring of  **`sourceText`.**                              |
| Example        | `substr("AbCDefghiJ KLMN",  2, 4)` returns `"CDef"`.                                         |

|                |                                                                             |
|----------------|-----------------------------------------------------------------------------|
| Syntax         | `<string> str:           substr   ( < string> sourceText, <string> regex)`  |
| Extension Type | Function                                                                    |
| Description    |  Returns a new string that is a substring of  **`sourceText`.**             |
| Examples       | `substr("WSO2D efghiJ KLMN", '^WSO2(.*)')` returns `"WSO2D efghiJ KLMN"`.   |

|                |                                                                                                 |
|----------------|-------------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           substr   ( < string> sourceText, <string> regex,  <int> groupNumber )` |
| Extension Type | Function                                                                                        |
| Description    | Returns a new string that is a substring of  **`sourceText`.**                                  |
| Example        | `substr("WSO2 cep WSO2 XX E hi hA WSO2 heAllo",  'WSO2(.*)A(.*)',  2)` returns `" ello"`.       |

 

### Trim function

|                |                                                                                       |
|----------------|---------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           trim   ( < string> str)`                                     |
| Extension Type | Function                                                                              |
| Description    | Returns a copy of  **`str`** , with the leading and/or trailing white-spaces omitted. |
| Example        | `trim("  AbCDefghiJ KLMN  ")` returns `"AbCDefghiJ KLMN"`.                            |

 

### Unhexadecimal function

|                |                                                                                                                                                                                                                                                                |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           unhex   ( < string> str)`                                                                                                                                                                                                             |
| Extension Type | Function                                                                                                                                                                                                                                                       |
| Description    | This is the equivalent of the `unhex` function in mysql 5.0. `unhex(str)` interprets each pair of characters in `str` as a hexadecimal number. Also see [hex () string extension](https://docs.wso2.com/display/CEP420/Siddhi+Extensions#SiddhiExtensions-he). |
| Example        | `unhex("4d7953514c")` returns `"MySQL"`.                                                                                                                                                                                                                       |

 

### Upper Case function

|                |                                                                                                             |
|----------------|-------------------------------------------------------------------------------------------------------------|
| Syntax         | `<string> str:           upper ( <string> str)`                                                             |
| Extension Type | Function                                                                                                    |
| Description    | Converts the simple letters in the given input string (i.e.  **`str`** ) to the equivalent capital letters. |
| Example        | `upper("Hello World")` returns `"HELLO WORLD"`.                                                             |
