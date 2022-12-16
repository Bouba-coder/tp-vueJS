<script setup>
//import
import { reactive, provide } from 'vue'
import { values as formValues, setValueChange as setFormValuesChange } from './Providers'

const props = defineProps({
    initialValues: {
        type: Object,
        required: true
    },    
    onSubmit: {
        type: Function,
        required: true
    },
    validate: {
        type: Function,
        required: false
    },
    });

const values = reactive(props.initialValues);

//handle
const handleSubmit = () => {
    console.log("handleSubmit : ", props.onSubmit(values));
};

//set changes
const setValueChange = (e) => {
    const { name, value } = e.target;
    values[name] = value;
    console.log("setValueChange : ", values);
};

//provide
provide(formValues, setValueChange);
provide(setFormValuesChange, setValueChange)
</script>

<template>
    
    <div>
        <h1>Formik</h1>
    </div>
    <slot :values="values" :handleSubmit="handleSubmit" :setValueChange="setValueChange" > </slot>
</template>
