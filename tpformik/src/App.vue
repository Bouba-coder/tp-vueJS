<script setup>
import FormVue from './components/Form.vue';
import Field from './components/Field.vue';

import { reactive } from 'vue';


const initialValues = reactive({
    name: '',
    email: '',
    password: '',
});

const onSubmit = (values) => {
    console.log("onSubmit : ", values);
};

const validate = (values) => {
    console.log("validate : ", values);
};
</script>

<template>
  <div id="app"> TP vueJS </div>
    <FormVue :initialValues="initialValues" :onSubmit="onSubmit" :validate="validate">
        <template #default="{ values, handleSubmit, setValueChange }">
            <div>
                <Field name="name" as="input" type="text" :value="values.name" @input="setValueChange" />
                <Field name="email" as="input" type="email" :value="values.email" @input="setValueChange" />
                <Field name="password" as="input" type="password" :value="values.password" @input="setValueChange" />
                <button @click="handleSubmit">Submit</button>
            </div>
        </template>
    </FormVue>
</template>

