<template>
  <div class="app">
      <ul 
        v-for="job in jobs"
        :key="job.id"
        >
        <li>
          <h2>{{job.title}}</h2>
          <div>{{job.location}}</div>
          <div>{{job.salary}}</div>
        </li>
      </ul>
  </div>
</template>

<script lang="ts">
  import { defineComponent, reactive, toRefs, ref } from "vue";
  import {Job} from './types/Job'
  export default defineComponent({
    name: "App",
    components: {},
    setup() {
      const jobs = ref<Job[]>([
        {
            title: 'QA',
            location: 'Kiev',
            salary: 1000,
            id: 1
        },
        {
            title: 'Back-end',
            location: 'Kharkiv',
            salary: 2000,
            id: 3
        },
        {
            title: 'Front-end',
            location: 'Kiev',
            salary: 2000,
            id: 3
        }
      ])
      return { jobs }
    },
  });
</script>

<style lang="scss">
  ul, li {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }

  .btn {
    width: 140px;
    height: 42px;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    color: #fff;
    cursor: pointer;
  }

  .red {
    background-color: red;
  }

  .blue {
    background-color: blue;
  }
</style>
