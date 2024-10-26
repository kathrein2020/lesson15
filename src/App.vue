<script>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'

import UserName from './components/UserName.vue'
import MyButton from './components/MyButton.vue'
import MyButtonCounter from './components/MyButtonCounter.vue'
import MyInput from './components/MyInput.vue'
import MyWidget from './components/MyWidget.vue'


export default {
  name: 'App',

components:{
HelloWorld,
TheWelcome,

UserName,
MyButton,
MyButtonCounter,
MyInput,
MyWidget

},

  data(){
    return{
      firstName: '',
      lastName: '',
      thirdName: '',
      isAgreed: false,
      selectedFruits: [],
      isTextVisible: false,
      counter: 0,
      selectedComponent: 'TheWelcome',
      tabs: ['HelloWorld', 'TheWelcome']
    }
  },

  methods: {
    submitForm(e) {
      e.preventDefault()
      console.log('Form submitted', this.firstName, this.lastName, this.isAgreed)
      console.log(this.selectedFruits)
    },

    toggleText(){
      this.isTextVisible = !this.isTextVisible
    },

addCounter(num){
  this.counter +=num
}

  },


  computed: {
    isUserAgreed(){
      return this.isAgreed ?  'Agree' : 'not Agree' 
    },

    isFruitSelected(){
      return this.selectedFruits.length > 0 ? 'Выбрано фруктов:' + this.selectedFruits.join(', ') : 'Выберите фрукты'
    }
  },

watch: {
  isAgreed(value) {
    if (!value) {
      alert('нуzhно согласие на обратку')
    } else{
      alert('спасибо за согласие')
    }
  }
},

provide() { 
  return {
  thirdName: 'this.thirdName'
  }
}

}

</script>


<template>
  <header>
    <!-- <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" /> -->

    <div class="wrapper">
      <!-- <HelloWorld msg="You did it!" /> -->
       <form action="" @submit="submitForm">
        <!-- <input type="text" placeholder="name" v-model.lazy="firstName"> -->
        <input type="text" placeholder="lastname" v-model.trim="lastName">
        <input type="checkbox" v-model="isAgreed"> Agree
 
        <MyInput title="Имя" v-model.lazy="firstName"/>
        <MyInput title="введите email"/>

      <div>
        <input type="checkbox" name="fruits" value="apple" v-model="selectedFruits"> Apple
        <input type="checkbox" name="fruits" value="pineapple" v-model="selectedFruits"> Pineapple
        <input type="checkbox" name="fruits" value="banana" v-model="selectedFruits"> Banana
      </div>

        <input type="submit">
       </form>

      <UserName :firstName="firstName" :lastName="lastName"/>
      <!-- компонент -->

      <br>
       
<!-- <p>{{ firstName }} {{ lastName }}</p> -->

<!-- <p>{{ isAgreed ? 'Agree' : 'not Agree' }}</p> -->

<p>{{ isUserAgreed }}</p>

<p>{{ isFruitSelected}}</p>

<p v-show="isTextVisible"> Скрытый текст</p>

<!-- <button @click="toggleText">Скрыть/показать текст</button> -->


<MyButton @click-event="toggleText">
<!-- использование emit для вызова из родителя -->

any  text for Slot
</MyButton>


<MyButton @click-event="toggleText">
Second text for Slot
</MyButton>


<p>{{ counter }}</p>
<MyButtonCounter @click-event="addCounter"/>


</div> 



  </header>

  <main>

   <!-- <TheWelcome />  -->

   <MyWidget :firstName ="firstName" :lastName="lastName">
    <template #header>
      <h3>заголовок</h3>
    </template>
 
   <p>текст</p>

   <template #footer>
    <a href="">ссылка</a>
   </template>

   </MyWidget>

   <MyWidget>
   <h3>заголовок</h3>
   <p>текст</p>
   <p>текст</p>
   </MyWidget>

   <!-- <MyWidget/>
   <MyWidget/> -->

<!-- добавление компонента -->
   <component is="HelloWorld"/>

   <!-- добавление динамическго компонента -->
   <component :is="selectedComponent"/>
  
  </main>

   <button v-for="tab in tabs" @click="selectedComponent = tab">{{ tab }}</button>


</template>



<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
