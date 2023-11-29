<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResource from './components/resource/TheResource.vue';

export default {
  components: { TheHeader, TheResource },
};
</script>

<template>
  <the-header title="Remember Me" />
  <the-resource />
</template>
