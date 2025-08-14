<script setup>
import {ref,reactive} from 'vue'
import {validate,clean_errors,add_validator,DjError} from 'djvalidatorvue'

let text_errors=reactive({})
let text_obj=reactive({
    text:"",
    word:"",
    atext:"",
    antext:""
})
let text_rules={
    text:{req:true,rule:"text,2,4"},
    word:{req:true,rule:"word,2,4"},
    atext:{req:true,rule:"atext,2,4"},
    antext:{req:true,rule:"antext,2,4"}
}
function validate_text(){
    alert(validate(text_obj,text_rules,text_errors))
}

let num_errors=reactive({})
let num_obj=reactive({
    dig:"",
    int:null,
    num:null,
})
let num_rules={
    dig:{req:true,rule:"dig,4,8"},
    int:{req:true,rule:"int,1,100"},
    num:{req:true,rule:"num,1,100"},
}
function validate_num(){
    alert(validate(num_obj,num_rules,num_errors))
}

let com_errors=reactive({})
let com_obj=reactive({
    email:"",
    url:"",
    ip:"",
    phone:"",
})
let com_rules={
    email:{req:true,rule:"email,50"},
    url:{req:true,rule:"url,50"},
    ip:{req:true,rule:"ip,v4"},
    phone:{req:true,rule:"phone"},
}
function validate_com(){
    alert(validate(com_obj,com_rules,com_errors))
}

let file_errors=reactive({})
let file_obj=reactive({
    file:null,
})
function handleFileUpload(event) {
    file_obj.file=event.target.files
}
let file_rules={
    file:{req:true,rule:"file,2,4,10,100,image/jpeg|image/png|image/bmp"},
}
function validate_file(){
    alert(validate(file_obj,file_rules,file_errors))
}

let select_errors=reactive({})
let select_obj=reactive({
    array:[],
})
let select_rules={
    array:{req:true,rule:"array,2,4"},
}
function validate_select(){
    alert(validate(select_obj,select_rules,select_errors))
}

let check_errors=reactive({})
let check_obj=reactive({
    radio:null,
    check:null,
    checkg:[],
})
let check_rules={
    radio:{req:true},
    check:{req:true},
    checkg:{req:true,rule:"array,2,3"},
}
function validate_check(){
    alert(validate(check_obj,check_rules,check_errors))
}

let rel_errors=reactive({})
let rel_obj=reactive({
    inputa:"",
    inputb:"",
    inputc:"",
    inputd:"",
    inpute:"",
    inputf:"",
    inputg:"",
    inputh:"",
})
let rel_rules={
    inputa:{req:true},
    inputb:{rule:"equal,inputa"},
    inputc:{req:true},
    inputd:{rule:"nequal,inputc"},
    inpute:{rule:"and,inputf"},
    inputg:{rule:"or,inputh"},
}
function validate_rel(){
    alert(validate(rel_obj,rel_rules,rel_errors))
}

let custom_errors=reactive({})
let custom_obj=reactive({
    regular:"",
    func:"",
    newrule:"",
})
let custom_rules={
    regular:{req:true,rule:"regexp,^[aeiou]+$,i",msg:"only vocals"},
    func:{req:true,rule:"call",func:isUpperCase,msg:"It is not uppercase"},
    newrule:{req:true,rule:"even,10"},
}
function isUpperCase(value,params){
    return value.toUpperCase()===value
}
function isEven(name,model,params){
    let value=model[name]
    if(!isNaN(value)){
        let data=parseInt(value)
        if(data%2!=0||data>params[1])return false
        else return true
    }
    return false
}
add_validator('even',isEven,'it is not an even number less than $1')
function validate_custom(){
    alert(validate(custom_obj,custom_rules,custom_errors))
}

function clean(){
    clean_errors(text_errors)
    clean_errors(num_errors)
    clean_errors(com_errors)
    clean_errors(file_errors)
    clean_errors(select_errors)
    clean_errors(check_errors)
    clean_errors(rel_errors)
    clean_errors(custom_errors)
}
</script>
<template>
    <h4>DjValidator catalog</h4>
    <button type="button" id="clean" @click="clean" class="btn btn-primary">Clean form validation messages.</button>
    <div class="row">
        <div class="panel panel-default col-md-6">
            <div class="panel-body">
                <form id="form" class="form-horizontal">
                    <fieldset>

                        <legend>Text inputs</legend>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textarea">Text (text)</label>
                                <textarea class="form-control input-sm" placeholder="text,4,8" v-model="text_obj.text"></textarea>
                            <DjError :error="text_errors.text"/>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="passwordinput">Word (word)</label>
                                <input class="form-control input-sm" type="password" placeholder="word,4,8" v-model="text_obj.word">
                            <DjError :error="text_errors.word"/>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Alphabetic text (atext)</label>
                                <input class="form-control input-sm" type="text" placeholder="atext,3,12" v-model="text_obj.atext">
                            <DjError :error="text_errors.atext"/>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Alphabetic and numeric text
                                (antext)</label>
                                <input name="textinput" type="text" placeholder="antext,3,12" class="form-control input-md" v-model="text_obj.antext">
                            <DjError :error="text_errors.antext"/>
                        </div>

                    </fieldset>

                    <div class="form-group mb-3">
                        <label class="control-label" for="singlebutton"></label>
                            <button type="button" class="btn btn-primary" @click="validate_text">Validate!</button>
                    </div>

                </form>
            </div>
        </div>

        <div class="panel panel-default col-md-6">
            <div class="panel-body">
                <form id="form2" class="form-horizontal">
                    <fieldset>

                        <legend>Numeric inputs</legend>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Digits (dig)</label>
                                <input name="textinput" type="text" placeholder="dig,4,8" class="form-control input-md" v-model="num_obj.dig">
                                <DjError :error="num_errors.dig"/>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Integer (int)</label>
                                <input name="textinput" type="text" placeholder="int,1,100" class="form-control input-md" v-model="num_obj.int">
                                <DjError :error="num_errors.int"/>
                        </div>

                        <!-- Text input-->
                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Real (num)</label>
                                <input name="textinput" type="text" placeholder="num,1,10" class="form-control input-md"  v-model="num_obj.num">
                                <DjError :error="num_errors.num"/>
                        </div>

                    </fieldset>

                    <div class="form-group">
                        <label class="control-label" for="singlebutton"></label>
                            <button type="button" @click="validate_num"
                                class="btn btn-primary">Validate!</button>
                    </div>

                </form>
            </div>
        </div>

        <div class="panel panel-default col-md-6">
            <div class="panel-body">
                <form id="form3" class="form-horizontal">
                    <fieldset>

                        <legend>Common validators</legend>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Email (email)</label>
                                <input name="textinput" type="text" placeholder="email,50" class="form-control input-md" v-model="com_obj.email">
                                <DjError :error="com_errors.email"/>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Url (url)</label>
                                <input name="textinput" type="text" placeholder="url,50" class="form-control input-md" v-model="com_obj.url">
                                <DjError :error="com_errors.url"/>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">IP (ip)</label>
                                <input name="textinput" type="text" placeholder="ip,v4" class="form-control input-md" v-model="com_obj.ip">
                                <DjError :error="com_errors.ip"/>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Phone number (phone)</label>
                                <input name="textinput" type="text" placeholder="phone" class="form-control input-md" v-model="com_obj.phone">
                                <DjError :error="com_errors.phone"/>
                        </div>

                    </fieldset>

                    <div class="form-group">
                        <label class="control-label" for="singlebutton"></label>
                            <button type="button" class="btn btn-primary" @click="validate_com">Validate!</button>
                    </div>

                </form>
            </div>
        </div>
        <div class="panel panel-default col-md-6">
            <div class="panel-body">
                <form id="form4" class="form-horizontal">
                    <fieldset>

                        <legend>File validators</legend>

                        <div class="form-group">
                            <label class="control-label" for="filebutton">File (file)</label>
                                <input type="file" multiple @change="handleFileUpload">
                                <DjError :error="file_errors.file"/>
                                <span class="help-block">rule: file,2,4,10,100,image/jpeg|image/png|image/bmp</span>
                        </div>

                    </fieldset>

                    <div class="form-group">
                        <label class="control-label" for="singlebutton"></label>
                            <button type="button" @click="validate_file" class="btn btn-primary">Validate!</button>
                    </div>

                </form>
            </div>
        </div>
    </div>

    <div class="row mt-5">
        <div class="panel panel-default col-md-6">
            <div class="panel-body">
                <form id="form5" class="form-horizontal">
                    <fieldset>

                        <legend>Select field</legend>

                        <div class="form-group">
                            <label class="control-label" for="selectmultiple">Select Multiple (array)</label>
                                <select class="form-control" v-model="select_obj.array" multiple>
                                    <option value="1">Option one</option>
                                    <option value="2">Option two</option>
                                    <option value="3">Option tree</option>
                                    <option value="4">Option four</option>
                                    <option value="5">Option five</option>
                                    <option value="6">Option six</option>
                                </select>
                                <DjError :error="select_errors.array"/>
                                <span class="help-block">rule: array,2,4</span>
                        </div>

                    </fieldset>

                    <div class="form-group">
                        <label class="control-label" for="singlebutton"></label>
                            <button type="button" @click="validate_select"
                                class="btn btn-primary">Validate!</button>
                    </div>

                </form>
            </div>
        </div>
        <div class="panel panel-default col-md-6">
            <div class="panel-body">
                <form id="form6" class="form-horizontal">
                    <fieldset>

                        <legend>Radios and checkboxes</legend>

                        <div class="form-group">
                            <label class="control-label" for="radios">Radio required</label>
                                <div class="radio">
                                    <label for="radios-0">
                                        <input type="radio" name="radios" id="radios-0" value="1" v-model="check_obj.radio">
                                        Option one
                                    </label>
                                </div>
                                <div class="radio">
                                    <label for="radios-1">
                                        <input type="radio" name="radios" id="radios-1" value="2" v-model="check_obj.radio">
                                        Option two
                                    </label>
                                </div>
                                <div class="radio">
                                    <label for="radios-1">
                                        <input type="radio" name="radios" id="radios-1" value="3" v-model="check_obj.radio">
                                        Option tree
                                    </label>
                                </div>
                                <DjError :error="check_errors.radio"/>
                                <span class="help-block">{req: true}</span>
                        </div>

                        <div class="form-group mt-3">
                            <label class="control-label" for="checkboxes">Checkbox</label>
                                <div class="checkbox">
                                    <label for="checkboxes">
                                        <input type="checkbox" name="checkbox" value="true" v-model="check_obj.check">
                                        Check this
                                    </label>
                                </div>
                                <DjError :error="check_errors.check"/>
                                <span class="help-block">{req: true}</span>
                        </div>

                        <div class="form-group mt-3">
                            <label class="control-label" for="checkboxes">Checkbox group</label>
                                <div class="checkbox">
                                    <label for="checkboxes">
                                        <input type="checkbox" name="checkbox" value="1" v-model="check_obj.checkg">
                                        option 1
                                    </label>
                                    <label for="checkboxes">
                                        <input type="checkbox" name="checkbox" value="2" v-model="check_obj.checkg">
                                        option 2
                                    </label>
                                    <label for="checkboxes">
                                        <input type="checkbox" name="checkbox" value="3" v-model="check_obj.checkg">
                                        option 3
                                    </label>
                                </div>
                                <span class="help-block">rule: array,2,3</span>
                                <DjError :error="check_errors.checkg"/>
                        </div>

                    </fieldset>

                    <div class="form-group">
                        <label class="control-label" for="singlebutton"></label>
                            <button type="button" @click="validate_check"
                                class="btn btn-primary">Validate!</button>
                    </div>

                </form>
            </div>
        </div>
    </div>

    <div class="row">
        <div class="panel panel-default col-md-6">
            <div class="panel-body">
                <form id="form7" class="form-horizontal">
                    <fieldset>

                        <legend>Related fields</legend>

                        <div class="form-group">
                            <label class="control-label" for="textinput">input a</label>
                                <input id="a" name="textinput" type="text"
                                    class="form-control input-md" v-model="rel_obj.inputa">
                                <DjError :error="rel_errors.inputa"/>
                        </div>

                        <div class="form-group mb-4">
                            <label class="control-label" for="textinput">input b (equal,inputa)</label>
                                <input name="textinput" type="text" placeholder="equal,inputa"
                                    class="form-control input-md" v-model="rel_obj.inputb">
                                <DjError :error="rel_errors.inputb"/>
                        </div>

                        <div class="form-group">
                            <label class="control-label" for="textinput">input c</label>
                                <input id="c" name="textinput" type="text" 
                                    class="form-control input-md" v-model="rel_obj.inputc">
                                <DjError :error="rel_errors.inputc"/>
                        </div>

                        <div class="form-group mb-4">
                            <label class="control-label" for="textinput">input d (not equal,inputc)</label>
                                <input name="textinput" type="text" placeholder="nequal,inputc"
                                    class="form-control input-md" v-model="rel_obj.inputd">
                                <DjError :error="rel_errors.inputd"/>
                        </div>

                        <div class="form-group">
                            <label class="control-label" for="textinput">input e</label>
                                <input name="textinput" type="text" placeholder="and,f" class="form-control input-md"
                                    v-model="rel_obj.inpute">
                        </div>

                        <div class="form-group mb-4">
                            <label class="control-label" for="textinput">input f (and)</label>
                                <input name="textinput" type="text" placeholder="" class="form-control input-md"
                                    v-model="rel_obj.inputf">
                                <DjError :error="rel_errors.inpute"/>
                        </div>

                        <div class="form-group">
                            <label class="control-label" for="textinput">optional input g</label>
                                <input name="textinput" type="text" placeholder="or,h" class="form-control input-md"
                                    v-model="rel_obj.inputg">
                        </div>

                        <div class="form-group">
                            <label class="control-label" for="textinput">optional input h (or)</label>
                                <input name="textinput" type="text" placeholder="" class="form-control input-md"
                                    v-model="rel_obj.inputh">
                                <DjError :error="rel_errors.inputg"/>
                        </div>

                    </fieldset>

                    <div class="form-group mt-3">
                        <label class="control-label" for="singlebutton"></label>
                            <button type="button" @click="validate_rel" class="btn btn-primary">Validate!</button>
                    </div>

                </form>
            </div>
        </div>

        <div class="panel panel-default col-md-6">
            <div class="panel-body">
                <form id="form8" class="form-horizontal">
                    <fieldset>

                        <legend>Custom validations</legend>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Regular expression (regexp)</label>
                            <div>
                                <input name="textinput" type="text" placeholder="regexp,^[aeiou]+$,i"
                                    class="form-control input-md" v-model="custom_obj.regular">
                                <DjError :error="custom_errors.regular"/>
                            </div>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Custom function (call uppercase function)</label>
                                <input name="textinput" type="text" placeholder="call,isUpperCase"
                                    class="form-control input-md" v-model="custom_obj.func">
                                <DjError :error="custom_errors.func"/>
                        </div>

                        <div class="form-group mb-3">
                            <label class="control-label" for="textinput">Custom rule added ('even,[max]')</label>
                                <input name="textinput" type="text" placeholder="even,10" class="form-control input-md"
                                    v-model="custom_obj.newrule">
                                <DjError :error="custom_errors.newrule"/>
                        </div>

                    </fieldset>

                    <div class="form-group">
                        <label class="control-label" for="singlebutton"></label>
                            <button type="button" @click="validate_custom"
                                class="btn btn-primary">Validate!</button>
                    </div>

                </form>
            </div>
        </div>
    </div>
</template>