<template>
    <h3><b>Validator translation</b></h3><br>
    <p>To translate messages to any language, use the "set_messages" function on main.js, passing all the translated tags.</p>
    <pre>	    	
        import {set_messages} from 'djvalidatorvue'

        let spanish={
            required: 'Campo requerido.',
            word_min: 'Por lo menos $1 caracteres sin espacios.',
            word_between: 'Entre $1 y $2 caracteres sin espacios.',
        }
        set_messages(spanish)
    </pre>
    <p>Spanish and Russian translations are included in the 'locale' folder.</p>
    <p>Example to spanish (in main.js):</p>
    <pre>	    	
        import {set_messages} from 'djvalidatorvue'
        import messages from 'djvalidatorvue/locale/djValidatorvue_es'

        set_messages(messages)
    </pre>
    <p>To russian:</p>
    <pre>	    	
        import {set_messages} from 'djvalidatorvue'
        import messages from 'djvalidatorvue/locale/djValidatorvue_ru'
        
        set_messages(messages)
    </pre>
</template>