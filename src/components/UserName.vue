<script>
export default {
    name: 'UserName',
    props: ['firstName', 'lastName']
     
}
</script>

<template>
    <p style=" font-weight: bold;">{{ firstName}} {{lastName }}</p>
    </template>