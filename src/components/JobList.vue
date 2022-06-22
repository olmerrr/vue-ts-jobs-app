<template>
  <div>
      <transition-group 
        name='list'
        v-if="orderedJobs"
        tag="ul"
        >
        <li class="item" v-for="job in orderedJobs" :key="job.id">
          <h2>{{ job.title }}</h2>
          <div>{{ job.location }}</div>
          <div><b>{{ job.salary }}</b> $</div>
        </li>
      </transition-group>
  </div>
</template>
<script lang="ts">
  import { computed, defineComponent, PropType } from "vue";
  import { Job } from "@/types/Job";
  import { OrderTerm } from "@/types/OrderTerm";

  export default defineComponent({
    props: {
      jobs: {
        required: true,
        type: Array as PropType<Job[]>,
      },
      order: {
        required: true,
        type: String as PropType<OrderTerm>,
      },
    },
    setup(props) {
      const orderedJobs = computed(() => {
        return [...props.jobs].sort((a: Job, b: Job) => {
          return a[props.order] > b[props.order] ? 1 : -1;
        });
      });

      return { orderedJobs };
    },
  });
</script>

<style lang="scss">
  .item {
    margin-top: 16px;
    padding: 8px;
    background-color: #fff;
    border-radius: 4px;
  }

  .list-move {
    transition: all 1s;
  }
</style>
