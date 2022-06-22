<template>
  <div>
    <ul v-if="jobs">
      <li v-for="job in jobs" 
          :key="job.id">
        <h2>{{ job.title }}</h2>
        <div>{{ job.location }}</div>
        <div>{{ job.salary }}</div>
      </li>
    </ul>
  </div>
</template>
<script lang="ts">
  import { defineComponent, PropType } from "vue";
  import { Job } from '@/types/Job'

  export default defineComponent({
    props: {
      jobs: {
        required: true,
        type: Array as PropType<Job[]>
      }
    }
  });
</script>

<style lang="scss"></style>
