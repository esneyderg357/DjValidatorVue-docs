<template>
    <h3><b>DjError for invalid feedback</b></h3>
    For added convenience you can use the built-in component 'DjError' to show invalid feedback
    <br><br>
    <pre v-pre>
        import {DjError} from 'djvalidatorvue'

        let errors=ref({})
        let mi_obj=reactive({
            email:""
        })
        
    </pre>
    On template:
    <pre>
        &lt;input type="text" v-model="mi_obj.email"&gt;
        &lt;DjError :error="errors.email"/&gt;
    </pre>
    <br>
    <h5>Properties</h5>
    <ul>
        <li>Error: The error variable to show (is the same name as the property)</li>
    </ul>
    <br>
    <h5>Customize style</h5>
    <p>The component uses the "dj-validator-msg" class for styles.</p>
    <p>You can customize style with CSS variables:</p>
    <code>
        <ul>
            <li>--dj-validator-error-color:red</li>
            <li>--dj-validator-text-size:.8rem</li>
        </ul>
    </code>
</template>