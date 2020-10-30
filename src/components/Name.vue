<template>
    <div class="name">
        <label>Name</label>
        <input 
            type="text"
            v-model.trim="$v.name.$model"
            :class="{
                'is-invalid':$v.name.$error, 'is-valid': !$v.name.$invalid
            }"
        >
        <!--<div class="valid">Your name is valid</div>-->
        <div class="invalid">
            <span v-if="!$v.name.required"> ! Your name is required</span>
            <span v-if="!$v.name.minLength"> ! Your name must have at least 
                {{$v.name.$params.minLength.min}} letters
            </span>
            <span v-if="!$v.name.maxLength">! Your name must have at most 
                {{$v.name.$params.maxLength.max}} letters
            </span>
        </div>
    </div>
</template>

<script>
import {required, minLength, maxLength } from "vuelidate/lib/validators"
export default {
    name: "name",
    data() {
        return {
            name: ""
        }
    },
    validations: {
        name: {
            required, 
            minLength: minLength(3),
            maxLength: maxLength(10)
        }
    }
}

</script>

<style scoped>
    .name {
        display:flex;
        flex-direction: column;
        margin: 5px;
    }
    label {
        font-size: 25px;
        font-weight: bold;
        margin: 5px;  
    }
    input {
        font-size: 25px;
        margin: 5px;
    }
    span {
        color: #f91b1b;
        font-size: 25px;
    }

</style>