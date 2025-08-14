<script setup>
import { reactive,ref } from 'vue';
import {validate,DjError} from 'djvalidatorvue'

let result=ref(null)
let data=reactive({
    email:"",
    username:""
})
let validation={
    email:{req:true,rule:'email,30'},
    username:{req:true,rule:'word,4,20'}
}
let errors=reactive({})

function test(){
    result=validate(data,validation,errors)
}
</script>
<template>
    <h5>DjValidatorVue is the most simple, flexible and quick to use library for vue3 validation, it does not depend on any UI.
Available with translations.</h5>
<br>
    <div class="col-6">
        <label class="control-label" for="passwordinput">Username</label>
        <input class="form-control input-sm" type="text" v-model="data.username">
        <DjError :error="errors.username"/>
    </div>
    <div class="col-6 mt-3 mb-2" >
        <label class="control-label" for="textinput">Email (email)</label>
        <input name="textinput" type="text" class="form-control input-md" v-model="data.email">
        <DjError :error="errors.email"/>
    </div>
    <button class="btn btn-primary" @click="test">Test!</button>
    <p>Resultado: {{result}}</p>
    <br>
<h5>Features</h5>
<ul>
    <li>Model based validator</li>
    <li>Simple and quick validation rules</li>
    <li>Minimum code</li>
    <li>Integration with any type of vue project</li>
    <li>Optional custom component for messages</li>
    <li>You can create your own validators</li>
    <li>Without dependency</li>
    <li>UI independent</li>
</ul>
<br>
<h5>Details</h5>
<ul>
    <li>Validate Objects</li>
    <li>Validate only a field</li>
    <li>Validate simple variable</li>
    <li>Several validation rules</li>
    <li>Defult labels</li>
    <li>Customize labels</li>
    <li>Translation</li>
    <li>Custom invalid feedback component</li>
    <li>Customize and add validators</li>
</ul>

<p>DjValidatorVue is based on classic <a href="https://www.npmjs.com/package/djvalidator">DjValidator jquery plugin</a></p>
<p>DjValidatorVue was written by David Esneyder Jerez Garnica.</p>

<a href="https://www.linkedin.com/in/david-esneyder-jerez-garnica-84309b239/">Linkedin</a><br>
<a href="hmailto:esneyderg357@gmail.com">esneyderg357@gmail.com</a>

<p>Copyright (c) 2025 Released under the GPL v3 license.</p>

</template>