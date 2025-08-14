<template>
    <h3><b>Validator label reference</b></h3>
    <p>Following labels contain the validation messages for each key, these can be changed at any time:</p>
    <pre>	    	
        import {set_messages} from 'djvalidatorvue'

        let my_msg={
            required: 'Required',
            word_min: 'min: $1 character',
            word_between: 'min: $1 character,max: $2 characters',
        }
        set_messages(my_msg)
    </pre>
    <table class="table table-bordered table-striped">
        <tbody>
            <tr class="text-center">
                <td><strong>Label</strong></td>
                <td><strong>Description</strong></td>
            </tr>
            <tr>
                <td>
                    <p>required</p>
                </td>
                <td>
                    <p>Required</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>word_min</p>
                </td>
                <td>
                    <p>Word, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>word_between</p>
                </td>
                <td>
                    <p>Word, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>atext_min</p>
                </td>
                <td>
                    <p>atext, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>atext_between</p>
                </td>
                <td>
                    <p>atext, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>antext_min</p>
                </td>
                <td>
                    <p>antext, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>antext_between</p>
                </td>
                <td>
                    <p>antext, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>text_min</p>
                </td>
                <td>
                    <p>text, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>text_between</p>
                </td>
                <td>
                    <p>text, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>int_invalid</p>
                </td>
                <td>
                    <p>int, when it is not a valid integer</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>int_min</p>
                </td>
                <td>
                    <p>int, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>int_max</p>
                </td>
                <td>
                    <p>int, when the minimum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>int_between</p>
                </td>
                <td>
                    <p>int, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>num_invalid</p>
                </td>
                <td>
                    <p>num, when it is not a valid number</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>num_min</p>
                </td>
                <td>
                    <p>num, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>num_max</p>
                </td>
                <td>
                    <p>num, when the minimum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>num_between</p>
                </td>
                <td>
                    <p>num, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>dig_min</p>
                </td>
                <td>
                    <p>dig, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>dig_between</p>
                </td>
                <td>
                    <p>dig, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>file_min</p>
                </td>
                <td>
                    <p>file, when the maximum amount is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>file_between</p>
                </td>
                <td>
                    <p>file, without skipping quantities</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>file_format</p>
                </td>
                <td>
                    <p>file, when it is not a valid format</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>file_min_size</p>
                </td>
                <td>
                    <p>file, when the minimum size is specified</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>file_max_size</p>
                </td>
                <td>
                    <p>file, when the maximum size is specified</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>email</p>
                </td>
                <td>
                    <p>email, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>email_max</p>
                </td>
                <td>
                    <p>email, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>phone</p>
                </td>
                <td>
                    <p>phone, when it is not valid</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>url</p>
                </td>
                <td>
                    <p>url, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>url_max</p>
                </td>
                <td>
                    <p>url, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>ip</p>
                </td>
                <td>
                    <p>ip, when it is not a valid IP</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>array_min</p>
                </td>
                <td>
                    <p>array, when the maximum is omitted</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>array_between</p>
                </td>
                <td>
                    <p>array, without omissions</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>and</p>
                </td>
                <td>
                    <p>and, when both fields are filled</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>or</p>
                </td>
                <td>
                    <p>or, when no field is filled</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>equal</p>
                </td>
                <td>
                    <p>equal, when the fields are different</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>not_equal</p>
                </td>
                <td>
                    <p>nequal, when the fields are equal</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>regexp</p>
                </td>
                <td>
                    <p>regexp, when it does not meet the expression</p>
                </td>
            </tr>
            <tr>
                <td>
                    <p>call</p>
                </td>
                <td>
                    <p>call, call to a user function</p>
                </td>
            </tr>
        </tbody>
    </table>
</template>