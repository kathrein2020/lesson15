<script>

import UserName from './UserName.vue';

export default{
    name:'MyWidget',
    components: {
        UserName
    },

    props: {
        firstName: {
            type: String,
            required: true
        },
        lastName: {
            type: String,
            required: true
        }
    }
}
</script>

<template>
    <div class="widget">
<div class="widget-container">
    <div class="widget-header">
    <slot name="header"></slot>
</div>
<!-- <h3>заголовок</h3>
<p>текст</p>
<a href="">ссылка</a> -->

<slot> </slot>
<div class="widget-footer">
<slot name="footer"></slot>

<UserName :firstName="firstName" :lastName="lastName" />

</div>
</div>
</div>

</template>

<style>
.widget {
    background-color:  #f0f0f0;
    padding: 20px;
    border-radius: 5px;
}
.widget-container {
    background-color:  #fff;
    padding: 20px;
    border-radius: 5px;
}

.widget-header {
    background-color: aquamarine;
  margin-bottom: 20px;
}

.widget-footer {
    background-color: burlywood;
  margin-bottom: 20px;
}
</style>