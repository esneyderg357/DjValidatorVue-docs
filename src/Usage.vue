<template>
    <h3>Usage</h3>
    
    <br>
    <h4>Validate Object:</h4>

    <p>Use <b>'validate'</b> function, with 3 parameters: the object to validate, the instruction object, and the error object, this returns true or false as a result.</p>
    
    <pre v-pre>
    let resp=validate(mi_obj,validations,errors)
	alert(resp)//true or false
    </pre>
    
    <h5>Object to validate</h5>
    <p>Can be simple or reactive with any number of items:</p>
    <pre v-pre>
	let mi_obj=reactive({
		email:"",
		username: "",
		password: "",
		obs:""
	})
    </pre>
    <p>Also works with nested objects:</p>
    <pre v-pre>
	let mi_obj=reactive({
		email:"",
        user:{
            username: "",
            password: "",
        }
		obs:""
	})
    </pre>

    <h5>Instruction object</h5>
    <p>Contains the same keys as object to validate, each with the required validation rules, available options are:</p>
    <ul>
        <li>req (not required): Boolean, indicates if the field is required (default: false).</li>
        <li>rule (not required): String, the validation rule (review the available rules section).</li>
        <li>msg (not required): String, replaces the default invalid feedback rule messages.</li>
        <li>func (not required): Function, Only used by the 'call' rule, specifies an own or external validation function.</li>
    </ul>
    <p>Example:</p>
    <pre v-pre>
	const validations={
		email:{rule:'email,50'}, 
		obs:{req:true},
		username:{req:true,rule:'word,4,20'},
		password:{req:true,rule:'word,6,20',msg:'invalid password'},
	}
    </pre>
    <p><b>It is possible to apply multiple validation rules to a field by placing an array in the instructions object.</b></p>
    <p>Example:</p>
    <pre v-pre>
	const validations={
		name:[{req:true,rule:'text,5,150'},{rule:'regexp,^[aeiou]+$,i'}]
	}
    </pre>
    <p>The rules are applied in order according to the array.</p>
    <p>The 'req' key will only be needed once to avoid checking multiple times.</p>
    <br>
    <h5>Errors object</h5>
    <p>A empty reactive object, it will contain all invalid feedback (messages) with the same key as the corresponding item.<br>
    The object only contain keys with invalid feedback, the rest will be undefined.</p>
    <pre v-pre>
	let errors=reactive({})
    </pre>  
    <p>After call 'validate' it looks like this:</p>
    <pre v-pre>
	{email:'this field is required',username:'at least 4 letters',password:'invalid password'}
    </pre>  
   <p>This object is cleaned when call 'validate' again, to clean manually use 'clean_errors'</p>


    <br>
    <h4>Validate only a Field</h4>

    <p>Use <b>'validate_field'</b> function, with 4 parameters: key to validate, the main object, the instruction object, and the error object, this returns true or false as a result.<br>
    The operation is the same as validating an object.</p>

    <pre v-pre>
    let resp=validate_field('email',mi_obj,validations,errors)
	alert(resp)//true or false for 'email'
    </pre>

   <p>This function can be attached to perform validation with events such as blur or keyup.</p>

    <pre v-pre>
        &lt;input type="text" v-model="mi_obj.email" @blur="validate_field('email',mi_obj,validations,errors)"&gt;
        &lt;span class="error" v-if="errors.email"&gt;{{errors.email}}&lt;/span&gt;
    </pre>
    
    <br>
    <h4>Validate a simple variable</h4>
    
    <p>Use <b>'validate_var'</b> function, with 3 parameters: variable to validate, instruction object, and error variable (String, simple or ref)<br>
    The operation is the same as validating an object.</p>

    <pre v-pre>
    let email='qwerty@gmail.com' 
    let error=ref(null)
    let resp=validate_var(email,{req:true,rule:'email,50'},error)
	alert(resp)//true or false for email
    </pre>

    <br>
    <h4>Show invalid feedback</h4>
    <p>Show using the 'errors' object, with the tag and style you prefer.</p>
    <pre v-pre>
        &lt;input type="text" v-model="mi_obj.email"&gt;
        &lt;span class="error" v-if="errors.email"&gt;{{errors.email}}&lt;/span&gt;
    </pre>
    <p>Or use the built-in 'DjError' component for convenience:</p>
    <pre v-pre>
        import {DjError} from 'djvalidatorvue'

        &lt;input type="text" v-model="mi_obj.email"&gt;
        &lt;DjError :error="errors.email"/&gt;
    </pre>
    <p><b>see the components section for more details</b></p>

    <br>
    <h4>Clean invalid feedback</h4>
    <p>You can delete invalid feedback manually with 'clean_errors'</p>

    <pre v-pre>
        import {clean_errors} from 'djvalidatorvue'
        let errors=reactive({})
        function open_form(){
            clean_errors(errors)
        }
    </pre>
</template>