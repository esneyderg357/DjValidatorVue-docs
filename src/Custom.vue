<template>
    <h3><b>Custom validations</b></h3><br>
    <p>You can perform custom validations in 3 different ways, depending on your needs:</p>
    <ul>
        <li><b>Using the "regexp" key:</b>
            <p>The validation key <b>“regexp” can be used</b> to perform custom validations based on a specified regular
                expression and the flags (specified separately) must be in string format (for use with RegExp object
                constructor):
            </p>
            <pre>
rule:"regexp,^[aeiou]+$,i"
	    			</pre>
            <p>If the regular expression has commas, they must be
                replaced by the <b>°</b> character (degree) to avoid errors:</p>
            <pre>	    
rule:"regexp,^[aeiou]{3°5}$,i"
	    			</pre>
            <br>
        </li>
        <li><b>Using a proper function:</b>
            <p>The <b>call</b> validation key allows validation by executing a user defined function,
                 use a 'func' item of type function to specify the validation function to execute.
            </p>
            <p>
                The function will receive the value of the field and the parameters.
            </p>
            <p>

            </p>
            <pre>{rule:"call" , func: isUpperCase}</pre>
            <p>Being the user function:</p>
            <pre>
                function isUpperCase(value,params){
                    return value.toUpperCase()===value
                }
			</pre>
        </li>
        <li><b>Adding a new validation rule</b>
            <p>The <b>add_validator</b> function allows add a new custom validation rule in library.</p>
            <p>The function receives 3 parameters: the rule name, the validation function and the default message.</p>
            <p>
The validation function will receive: the field to validate, the complete object to validate and rule parameters(comma-separated rule).</p>
            <pre>
import {add_validator} from 'djvalidatorvue'

//add validator:
add_validator('even',isEven,'it is not an even number less than $1')

//validation function:
function isEven(name,model,params){
    //get value:
    let value=model[name]
    //validate and return boolean
    if(!isNaN(value)){
        let data=parseInt(value)
        if(data%2!=0||data>params[1])return false
        else return true
    }
    return false
}
	    	</pre>
            <p>Then it can be used like any other rule:</p>
            <pre>{req:true,rule:"even,10"}</pre>

            <p>The parameters are passed in an array with position 0 being the name of the rule.</p>
            <p>For example in the previous function params is: ['even','10']</p>
        </li>
    </ul>
</template>