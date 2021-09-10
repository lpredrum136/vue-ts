<template>
  <!-- <div class="app">{{ state.name }} - {{ state.age }}</div>
  <button @click="changeName('zelda')">change name</button>
  <button @click="changeAge('35')">change name</button> -->

  <header>
    <div class="order">
      <button @click="handleClick('title')">Order by title</button>
      <button @click="handleClick('salary')">Order by salary</button>
      <button @click="handleClick('location')">Order by location</button>
    </div>
  </header>

  <Jobs :jobs="jobs" :order="order" />
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import { Job } from './types/Job';
import Jobs from './components/Jobs.vue';
import { OrderTerm } from './types/OrderTerm';

export default defineComponent({
  name: 'App',
  components: { Jobs },
  setup() {
    // const name = ref('Link')
    // const age = ref<string | number>(25)
    // const changeName = (newName: string) => {
    //   name.value = newName
    // }
    // const changeAge = (newAge: number | string) => {
    //   age.value = newAge
    // }

    // const state = ref<{ name: string; age: number | string }>({
    //   name: 'Link',
    //   age: 25
    // })

    // return {
    //   state
    // }

    const jobs = ref<Job[]>([
      { id: '1', title: 'farm worker', location: 'ranch', salary: 30000 },
      {
        id: '2',
        title: 'quarry man',
        location: 'death mountain',
        salary: 40000
      },
      { id: '3', title: 'flute worker', location: 'lost woods', salary: 50000 }
    ]);

    const order = ref<OrderTerm>('title');

    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  }
});
</script>

<style></style>
