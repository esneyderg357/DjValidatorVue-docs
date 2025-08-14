<template>
    <h3><b>Validations available</b></h3><br>

    <h4><b>Required field</b></h4>
    <p>To validate if a field is required, use the 'req' RULE as true or false (default: false) on rule instructions.</p>
    <pre>
        const validations={
		email:{rule:'email,50'},//not required
		obs:{req:false,rule:'text,5,150'},//not required
		username:{req:true,rule:'word,4,20'},//required
		password:{req:true,rule:'word,6,20',msg:'invalid password'},//required
	}
    </pre>
    <p>Remember to apply several rules to the same field you can pass them in array:</p>
    <pre>
        const validations={
            name:[{req:true,rule:'text,5,150'},{rule:'regexp,^[aeiou]+$,i'}]
        }
    </pre>

    <h4><b>Validate texts:</b></h4>
    <table class="table table-bordered table-striped">
        <tbody>
            <tr class="text-center">
                <td>
                    <p><strong>VALIDATION</strong></p>
                </td>
                <td>
                    <p><strong>RULE</strong></p>
                </td>
                <td>
                    <p><strong>PARAMETERS</strong></p>
                </td>
                <td>
                    <p><strong>DESCRIPTION</strong></p>
                </td>
                <td>
                    <p><strong>EXAMPLES</strong></p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>Any text</p>
                </td>
                <td nowrap="">
                    <p>text, <strong>[min]</strong> , <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>min</strong> : minimum characters allowed. <br>
                        <strong>max</strong> : maximum characters allowed.
                    </p>
                </td>
                <td>
                    <p>Accept any character, validating only length of text. The maximum size can be omitted (*).</p>
                </td>
                <td nowrap="">
                    <p><code>
			      		rule:"text,3,12"<br>
			        	rule:"text,3,*"</code></p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>Alphabetic text</p>
                </td>
                <td nowrap="">
                    <p>atext, <strong>[min]</strong> , <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>min</strong> : minimum characters allowed. <br>
                        <strong>max</strong> : maximum characters allowed.
                    </p>
                </td>
                <td>
                    <p>Accepts alphabetic characters in upper and lower case, including spaces, the letter ñ and
                        accented characters (á, é, í, ó, ú, ç, ü), also validating length of text. The maximum size can
                        be omitted (*).</p>
                </td>
                <td nowrap=""><code>
			      		rule:"atext,3,12"<br>
			        	rule:"atext,3,*"</code></td>
            </tr>
            <tr>
                <td>
                    <p>Alphabetical text and digits</p>
                </td>
                <td nowrap="">
                    <p>antext, <strong>[min]</strong> , <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>min</strong> : minimum characters allowed. <br>
                        <strong>max</strong> : maximum characters allowed.
                    </p>
                </td>
                <td>
                    <p>Accept upper and lower case alphabetic digits and characters, including spaces, the letter ñ and
                        the accented characters (á, é, í, ó, ú, ç, ü), also validating length of text. The maximum size
                        can be omitted (*).</p>
                </td>
                <td nowrap=""><code>
			      	rule:"antext,3,12"<br>
			        rule:"antext,3,*"</code></td>
            </tr>
            <tr>
                <td>
                    <p>Word (text without spaces)</p>
                </td>
                <td nowrap="">
                    <p>word, <strong>[min]</strong> , <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>min</strong> : minimum characters allowed. <br>
                        <strong>max</strong> : maximum characters allowed.
                    </p>
                </td>
                <td>
                    <p>Accept any character except spaces, also validating length of text. The maximum size can be
                        omitted (*).</p>
                </td>
                <td nowrap=""><code>
			      	rule:"word,4,8"<br>
			        rule:"word,4,*"</code></td>
            </tr>
            <tr>
                <td>
                    <p>Digits only</p>
                </td>
                <td>
                    <p>dig, <strong>[min]</strong> , <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>min</strong> : minimum number of digits allowed. <br>
                        <strong>max</strong> : maximum digits allowed.
                    </p>
                </td>
                <td>
                    <p>Accept a digit text, validating the length of the digit string. The maximum size can be omitted
                        (*).</p>
                </td>
                <td><code>
			      	rule:"dig,4,8"<br>
			        rule:"dig,4,*"</code></td>
            </tr>
        </tbody>
    </table><br>
    <h4><b>Validate number fields</b></h4>
    <table class="table table-bordered table-striped">
        <tbody>
            <tr class="text-center">
                <td>
                    <p><strong>VALIDATION</strong></p>
                </td>
                <td>
                    <p><strong>RULE</strong></p>
                </td>
                <td>
                    <p><strong>PARAMETERS</strong></p>
                </td>
                <td>
                    <p><strong>DESCRIPTION</strong></p>
                </td>
                <td>
                    <p><strong>EXAMPLES</strong></p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>Integer numbers</p>
                </td>
                <td nowrap="">
                    <p>int, <strong>[min]</strong> , <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>min</strong> : minimum value allowed. <br>
                        <strong>max</strong> : maximum value allowed.
                    </p>
                </td>
                <td>
                    <p>Accept only positive or negative integers (accept the "-" sign ), also validating the value of
                        the whole number. The maximum and/or minimum value of the number can be omitted (*).</p>
                </td>
                <td nowrap=""><code>rule:"int,1,*" <br>
			        rule:"int,*,100" <br>
			        rule:"int,*,*"<br>
			        rule:"int,-100,-1"<code></code></code></td>
            </tr>
            <tr>
                <td>
                    <p>Real numbers</p>
                </td>
                <td nowrap="">
                    <p>num, <strong>[min]</strong> , <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>min</strong> : minimum value allowed. <br>
                        <strong>max</strong> : maximum value allowed.
                    </p>
                </td>
                <td>
                    <p>Accept any type of real number, using the point (.) as decimal separator, accept "-" sign, also
                        validating the number value. The maximum and/or minimum value can be omitted (*).</p>
                </td>
                <td nowrap=""><code>rule:"num,1,*"<br>
			        rule:"num,*,10.5"<br>
			        rule:"num,*,*"<br>
			        rule:"num,-1.5,1.5"<code></code></code></td>
            </tr>
        </tbody>
    </table><br>
    <h4><b>Common validations</b></h4>
    <table class="table table-bordered table-striped">
        <tbody>
            <tr class="text-center">
                <td>
                    <p><strong>VALIDATION</strong></p>
                </td>
                <td>
                    <p><strong>RULE</strong></p>
                </td>
                <td>
                    <p><strong>PARAMETERS</strong></p>
                </td>
                <td>
                    <p><strong>DESCRIPTION</strong></p>
                </td>
                <td>
                    <p><strong>EXAMPLES</strong></p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>Email address</p>
                </td>
                <td nowrap="">
                    <p>email, <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>max</strong> : maximum characters allowed.</p>
                </td>
                <td>
                    <p>Accept valid email addresses of any domain level, also validating maximum number of characters
                        optionally(*).</p>
                </td>
                <td nowrap=""><code>rule:"email,30"<br>
			        rule:"email,*"<code></code></code></td>
            </tr>
            <tr>
                <td>
                    <p>Web address (url)</p>
                </td>
                <td nowrap="">
                    <p>url, <strong>[max]</strong></p>
                </td>
                <td>
                    <p><strong>max</strong> : maximum characters allowed.</p>
                </td>
                <td>
                    <p>Accepts URLs of the HTTP, HTTPS, FTP and FTPS protocols, also validating maximum number of
                        characters optionally(*).</p>
                </td>
                <td nowrap=""><code>rule:"url,50"<br>
			        rule:"url,*"<code></code></code></td>
            </tr>
            <tr>
                <td>
                    <p>Phone number</p>
                </td>
                <td nowrap="">
                    <p>phone</p>
                </td>
                <td>
                    <p><strong>NONE</strong></p>
                </td>
                <td>
                    <p>Accepts phone numbers in the following formats: <br>
                        +591 70229728 <br>
                        70229728 <br>
                        The "+" sign is optional, the separator can be "space" or "-", the code can have 2 to 3 digits
                        and the number can have 5 to 12 digits.</p>
                </td>
                <td nowrap=""><code>rule:"phone"<code></code></code></td>
            </tr>
            <tr>
                <td>
                    <p>IP adress</p>
                </td>
                <td nowrap="">
                    <p>Ip, <strong>[type]</strong></p>
                </td>
                <td>
                    <p><strong>type</strong> (optional): ipv4 or ipv6</p>
                </td>
                <td>
                    <p>Accepts IP addresses that can be v4 or v6 depending on the specified parameter, if not specified
                        verify both.</p>
                </td>
                <td nowrap=""><code>rule:"ip"<br>
			        rule:"ip,v4"<br>
			        rule:"ip,v6"</code></td>
            </tr>
        </tbody>
    </table><br>
    <h4><b>Validate files</b></h4>
    <table class="table table-bordered table-striped">
        <tbody>
            <tr class="text-center">
                <td>
                    <p><strong>VALIDATION</strong></p>
                </td>
                <td>
                    <p><strong>RULE</strong></p>
                </td>
                <td>
                    <p><strong>PARAMETERS</strong></p>
                </td>
                <td>
                    <p><strong>DESCRIPTION</strong></p>
                </td>
                <td>
                    <p><strong>EXAMPLES</strong></p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>Validate files</p>
                </td>
                <td>
                    <p>file, <strong>[min], [max], [min_size], [max_size], [type1 | type2 ..]</strong></p>
                </td>
                <td>
                    <p><strong>min</strong> : minimum number of files to select. <br>
                        <strong>max</strong> : maximum number of files to select <br>
                        <strong>min_size</strong> : Minimum size of selected files (kb). <br>
                        <strong>max_size</strong> : Maximum size of selected files (kb). <br>
                        <strong>type1 | type2 ..</strong> : <strong>Mime</strong> types allowed.
                    </p>
                </td>
                <td>
                    <p>Validate files based on the javascript file API (if not available, validation is not performed),
                        setting the minimum and maximum of selected files where maximum can be omitted (*), the maximum
                        and minimum size in kb. For each file where both can be omitted (*) and finally validate the
                        file type following the mime types specified as array (at least one is required).</p>
                </td>
                <td><code>rule:"file,2,4,10,100,<br>image/jpeg|image/png|image/bmp"<br>
			        rule:"file,1,*,1,1000,image/jpeg"<br>
			        rule:"file,1,3,*,*,image/jpeg|image/png"</code></td>
            </tr>
        </tbody>
    </table><br>
    <h4><b>Validate arrays</b></h4>
    <table class="table table-bordered table-striped">
        <tbody>
            <tr class="text-center">
                <td>
                    <p><strong>VALIDATION</strong></p>
                </td>
                <td>
                    <p><strong>RULE</strong></p>
                </td>
                <td>
                    <p><strong>PARAMETERS</strong></p>
                </td>
                <td>
                    <p><strong>DESCRIPTION</strong></p>
                </td>
                <td>
                    <p><strong>EXAMPLES</strong></p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>Array length</p>
                </td>
                <td>
                    <p>array, <strong>[min], [max]</strong></p>
                </td>
                <td>
                    <p><strong>min:</strong> minimum array length. <br>
                        <strong>max</strong> : maximum array length.
                    </p>
                </td>
                <td>
                    <p>Validate array length, the maximum can be omitted (*).</p>
                </td>
                <td><code>rule:"array,2,4"<br>
			        rule:"array,2,*"</code></td>
            </tr>
        </tbody>
    </table><br>
    <h4><b>Validate related fields</b></h4>
    <table class="table table-bordered table-striped">
        <tbody>
            <tr class="text-center">
                <td>
                    <p><strong>VALIDATION</strong></p>
                </td>
                <td>
                    <p><strong>RULE</strong></p>
                </td>
                <td>
                    <p><strong>PARAMETERS</strong></p>
                </td>
                <td>
                    <p><strong>DESCRIPTION</strong></p>
                </td>
                <td>
                    <p><strong>EXAMPLES</strong></p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>Equal fields</p>
                </td>
                <td nowrap="">
                    <p>equal, <strong>[other_field]</strong></p>
                </td>
                <td>
                    <p><strong>other_field</strong> : The other field to compare.
                    </p>
                </td>
                <td>
                    <p>Validate that the value of field is equal to that specified, [other_field] must be of field with which
                        you want to compare.</p>
                </td>
                <td><code>rule:"equal,password"</code></td>
            </tr>
            <tr>
                <td>
                    <p>Different fields</p>
                </td>
                <td nowrap="">
                    <p>nequal, <strong>[other_field]</strong></p>
                </td>
                <td>
                    <p><strong>other_field</strong> : The other field to compare.
                    </p>
                </td>
                <td>
                    <p>Validate that the value of field is different to that specified, [other_field] must be of field with which
                        you want to compare.</p>
                </td>
                <td><code>rule:"nequal,data1"</code></td>
            </tr>
            <tr>
                <td>
                    <p>And (both fields required or not)</p>
                </td>
                <td nowrap="">
                    <p>and, <strong>[other_field]</strong></p>
                </td>
                <td>
                    <p><strong>other_field</strong> : The other field to compare.
                    </p>
                </td>
                <td>
                    <p>Validates that neither or both fields are required.</p>
                </td>
                <td><code>rule:"and,citty"</code></td>
            </tr>
            <tr>
                <td>
                    <p>Or (Optional fields)</p>
                </td>
                <td nowrap="">
                    <p>or, <strong>[other_field]</strong></p>
                </td>
                <td>
                    <p><strong>other_field</strong> : The other field to compare.
                    </p>
                </td>
                <td>
                    <p>Validate that at least one field is not empty (required).</p>
                </td>
                <td><code>rule:"or,name2"</code></td>
            </tr>
        </tbody>
    </table><br>
    <h4><b>Custom validations</b></h4>
    <table class="table table-bordered table-striped">
        <tbody>
            <tr class="text-center">
                <td>
                    <p><strong>VALIDATION</strong></p>
                </td>
                <td>
                    <p><strong>RULE</strong></p>
                </td>
                <td>
                    <p><strong>PARAMETERS</strong></p>
                </td>
                <td>
                    <p><strong>DESCRIPTION</strong></p>
                </td>
                <td>
                    <p><strong>EXAMPLES</strong></p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>Validate a regular expression</p>
                </td>
                <td>
                    <p>regexp, <strong>[regular_expresion], [flags]</strong></p>
                </td>
                <td>
                    <p><strong>regular_expresion</strong> : regular expression to use. <br>
                        <strong>Flags</strong> (optional): flags of the regular expression.
                    </p>
                </td>
                <td>
                    <p>Accept field value according to specified regular expression and flags(specified separately),
                        must be in string format (for use with the RegExp object constructor). <br>
                        If the regular expression has commas (reserved operator), they must be replaced by the
                        character: <b>°</b> , to avoid errors.</p>
                </td>
                <td><code>rule:"regexp,^[aeiou]+$,i"<br>
			        rule:"regexp,^[aeiou]{3°5}$,i"</code><br></td>
            </tr>
            <tr>
                <td>
                    <p>Call an own validation function</p>
                </td>
                <td>
                    <p>call</p>
                </td>
                <td>
                    <p><strong>no parameters.</strong></p>
                </td>
                <td>
                    <p>Call a user function to perform the validation, use a 'func' item of type function
                         to specify the validation function to execute.</p>
                    <p>The function will receive the value of the field and the parameters.</p>
                </td>
                <td><code>{rule:"call" , func: isUpperCase}</code><br><br>
                    <code>function isUpperCase(value,params){return value.toUpperCase()===value}</code></td>
            </tr>
        </tbody>
    </table>
    Check the <b>custom validations section</b> section for more details.<br><br>
</template>