<template>
  <div>
    <div v-bind="objectOfAtrr">
      <p>Hello World</p>
      <h5>{{ pageTitle }}</h5>
      <h6>{{ myName }}</h6>
    </div>
    <div v-html="message"></div>
    <p>{{ message ? 'yes' : 'no' }}</p>

    <h2>{{ item.married }}</h2>
    <h6 v-for="items in item" :key="items">{{ item.age }}</h6>
    <button @[eventName]="changeTitle()">Change Title</button>
    <button @[eventName]="namChange()">Change Name</button>

    <div>
      {{ isemployeesPresent }}
      <p>{{ fullName }}</p>

      <button @click="increase()">Increse</button>
      <p>{{ counterData.counter }}</p>
      <button @click="decrease">Decrease</button>
      <p>The counter Data {{ evenOrOdd }}</p>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed, reactive, ref } from 'vue'
const message = '<h1>Hello Im from script </h1>'
const dynamicId = 'my-id'
const eventName = 'click'
// for attr binding//
const objectOfAtrr = {
  id: dynamicId,
  class: 'container'
}
//counter increase and decrease//
const counterData = reactive({
  counter: 0
})
// const counter = ref(0)
const increase = () => {
  counterData.counter++
}
const decrease = () => {
  counterData.counter--
}
const evenOrOdd = computed(() => {
  return counterData.counter % 2 == 0 ? 'Even' : 'Odd'
})

const item = reactive({
  age: 45,
  name: 'rmbabu',
  city: 'hyderabad',
  married: true
})
// at click change //
const myName = ref('Raju')
const pageTitle = ref("I'm Iron Man")
const changeTitle = () => {
  pageTitle.value = "i'm Groot"
  // pageTitle.value = pageTitle.value
  // alert("I'm Groot")
}
const namChange = () => {
  myName.value = 'Ponnamanda Raju'
}

//computed property//
const firstName = ref('Raju')
const lastName = ref('Ponnamanda')

const fullName = computed(() => {
  return firstName.value + '' + lastName.value
})
const employees = reactive(['emp1', 'emp2'])
const isemployeesPresent = computed(() => {
  return employees.length ? 'yes' : 'no'
})

//using getter and setter //
// const fullName = computed(()=>{
// get(){
//   return firstName.value + " " + lastName.value;
// },
// set(newValue){
// [firstName.value, lastName.value]=newValue.split(' ')
// }
// })
</script>

<style scoped></style>
