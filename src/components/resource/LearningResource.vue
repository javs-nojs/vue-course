<script>
import Wrapper from '../wrapper/Wrapper.vue';
import BaseButton from '../button/Button.vue';

export default {
  components: {
    Wrapper,
    BaseButton,
  },

  inject: ['removeResource'],
  props: ['id', 'title', 'description', 'link'],
};
</script>

<template>
  <li>
    <wrapper>
      <header>
        <h3>{{ title }}</h3>

        <base-button class="flat" @click="removeResource(id)"
          >Delete</base-button
        >
      </header>

      <p>{{ description }}</p>

      <nav>
        <a :href="link">View Resource</a>
      </nav>
    </wrapper>
  </li>
</template>

<style scoped>
li {
  margin: auto;
  max-width: 40rem;
}

header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h3 {
  font-size: 1.25rem;
  margin: 0.5rem 0;
}

p {
  margin: 0.5rem 0;
}

a {
  text-decoration: none;
  color: #ce5c00;
}

a:hover,
a:active {
  color: #c89300;
}
</style>
