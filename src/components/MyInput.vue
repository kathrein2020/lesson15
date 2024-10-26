<script>
export default{
    name: 'MyInput',
    props: ['title', 'modelValue'],
    emits: ['update: modelValue']
}
</script>

<template> 
    <input type="text" 
     :placeholder="title" 
     :value="modelValue" 
     @input="$emit('update:modelValue', $event.target.value)">
</template>