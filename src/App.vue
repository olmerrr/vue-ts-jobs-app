<template>
  <div class="app">
    <header>
      <section class="actions">
        <button class="btn" @click="handleClick('title')">
          Order by title
        </button>
        <button class="btn" @click="handleClick('salary')">
          Order by salary
        </button>
        <button class="btn" @click="handleClick('location')">
          Order by location
        </button>
      </section>
    </header>
    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
  import { defineComponent, ref } from "vue";
  import { Job } from "./types/Job";
  import { OrderTerm } from "./types/OrderTerm";
  import JobList from "./components/JobList.vue";
  export default defineComponent({
    name: "App",
    components: {
      JobList,
    },
    setup() {
      const jobs = ref<Job[]>([
        {
          title: "QA",
          location: "Lviv",
          salary: 1000,
          id: "1",
        },
        {
          title: "Back-end",
          location: "Kharkiv",
          salary: 2500,
          id: "2",
        },
        {
          title: "Front-end",
          location: "Kiev",
          salary: 2000,
          id: "3",
        },
        {
          title: "Fullstack",
          location: "Lviv",
          salary: 3000,
          id: "4",
        },
        {
          title: "Back-end",
          location: "Kiev",
          salary: 2400,
          id: "5",
        },
        {
          title: "Front-end",
          location: "Lviv",
          salary: 1800,
          id: "6",
        },
        {
          title: "PM",
          location: "Kiev",
          salary: 1000,
          id: "7",
        },
      ]);
      const order = ref<OrderTerm>("title");
      const handleClick = (term: OrderTerm) => {
        order.value = term;
      };
      return { jobs, handleClick, order };
    },
  });
</script>

<style lang="scss">
  ul,
  li {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  body {
    background-color: rgba(93, 93, 93, 0.133);
  }
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    margin: 0 auto;
    max-width: 1400px;
    display: flex;
    justify-content: center;
  }

  .btn {
    width: 180px;
    height: 42px;
    border: none;
    border-radius: 4px;
    font-size: 18px;
    font-weight: 500;
    cursor: pointer;
    background-color: transition;
    transition: background-color 300ms linear;

    &:hover {
      background-color: rgb(209, 201, 201);
    }
  }

  .red {
    background-color: red;
  }

  .blue {
    background-color: blue;
  }

  .actions {
    display: flex;
    justify-content: space-between;
    width: 600px;
  }
</style>
