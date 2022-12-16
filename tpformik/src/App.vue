<script setup>
import FormVue from './components/Form.vue';
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
<div id="app">
    <FormVue
    :initialValues="initialValues"
    :onSubmit="onSubmit"
    :validate="validate"
    >
        <template #default="{ values, errors, handleSubmit, setValueChange }">
            <div>
                <label for="name">Name</label>
                <input type="text" name="name" v-model="values.name" @change="setValueChange" />
                <p v-if="errors"> erreur signalé.</p>
            </div>
            <div>
                <label for="email">Email</label>
                <input type="email" name="email" v-model="values.email" @change="setValueChange" />
            </div>
            <div>
                <label for="password">Password</label>
                <input type="password" name="password" v-model="values.password" @change="setValueChange" />
            </div>
            <div>
                <button type="submit" @click="handleSubmit">Submit</button>
            </div>
        </template>
    </FormVue>
</div>
</template>

