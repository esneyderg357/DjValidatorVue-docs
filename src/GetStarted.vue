<script setup>
import {validate,DjError} from 'djvalidatorvue'

</script>
<template>
    <h4>Get Started</h4>
    <br>
    <h5>Install</h5>
    <code>
        npm install djvalidatorvue --save
    </code>
    <br><br>
    <h5>Import</h5>
    <code>
        import {validate} from 'djvalidatorvue'
    </code>
    <br><br>
    <h5>Using</h5>
    
    Having a simple or reactive object:
    <pre v-pre>
	
	let mi_obj=reactive({
		email:"",
		username: "",
		password: "",
		obs:""
	})
    </pre>

	Declare an object with validation instructions, with the same key as the object to be validated:
    <br><br>
    <pre v-pre>
	const validations={
		email:{rule:'email,50'}, 
		obs:{req:true,rule:'text,5,150'},
		username:{req:true,rule:'word,4,20'},
		password:{req:true,rule:'word,6,20',msg:'invalid password'},
	}
    </pre>

	Then declare object to contain invalid feedback(messages),this will contain only the items that fail:
    <br><br>
    <pre v-pre>
	let errors=reactive({})
    </pre>

	
    Finally, you can validate at any time using the validate function, which receives 3 parameters: the object to validate, 
    the instruction object, and the feedback object. This will return true or false and load the feedback object.
    <br><br>
    <pre v-pre>
	function save(){
		let resp=validate(mi_obj,validations,errors)
		alert(resp)//true or false
	}
    </pre>

        
    errors contains invalid feedback with the same key as the validated object, to show:
    <br><br>
    <pre v-pre>
        &lt;input type="text" v-model="mi_obj.email"&gt;
        &lt;span class="error" v-if="errors.email"&gt;{{errors.email}}&lt;/span&gt;
    </pre>
    For added convenience you can use the built-in component 'DjError'
    <br><br>
    <pre v-pre>
        import {DjError} from 'djvalidatorvue'

        &lt;input type="text" v-model="mi_obj.email"&gt;
        &lt;DjError :error="errors.email"/&gt;
    </pre>
</template>