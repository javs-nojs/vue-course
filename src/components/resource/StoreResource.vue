<script>
import LearningResource from './LearningResource.vue';

export default {
  inject: ['resource'],

  components: { LearningResource },
};
</script>

<template>
  <ul>
    <learning-resource
      v-for="{ id, title, description, link } in resource"
      :key="id"
      :id="id"
      :title="title"
      :description="description"
      :link="link"
    />
  </ul>
</template>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
  max-width: 40rem;
  margin: auto;
}
</style>
