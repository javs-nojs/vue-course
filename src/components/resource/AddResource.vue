<script>
import Wrapper from '../wrapper/Wrapper.vue';
import BaseButton from '../button/Button.vue';
import BaseDialog from '../dialog/Dialog.vue';

export default {
  components: { Wrapper, BaseButton, BaseDialog },

  inject: ['addResource'],

  data() {
    return {
      inputInvalid: false,
    };
  },

  methods: {
    handleSubmit() {
      const title = this.$refs.title.value;
      const description = this.$refs.description.value;
      const link = this.$refs.link.value;

      if (
        title.trim() === '' ||
        description.trim() === '' ||
        link.trim() === ''
      ) {
        this.inputInvalid = true;
        return;
      }

      this.addResource(title, description, link);
    },

    handleOkey() {
      this.inputInvalid = false;
    },
  },
};
</script>

<template>
  <base-dialog v-if="inputInvalid" title="Input Invalid" @click="handleOkey">
    <template #default>
      <p>Lorem ipsum dolor sit amet!</p>

      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Incidunt,
        explicabo voluptatem quidem veritatis molestiae at.
      </p>
    </template>

    <template #action>
      <base-button @click="handleOkey">Okey</base-button>
    </template>
  </base-dialog>

  <wrapper>
    <form @submit.prevent="handleSubmit">
      <div class="form-control">
        <label for="title">Title</label>
        <input ref="title" type="text" id="title" name="title" />
      </div>

      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          ref="description"
          name="description"
          id="description"
          cols="3"
        ></textarea>
      </div>

      <div class="form-control">
        <label for="link">Title</label>
        <input ref="link" type="url" id="link" name="link" />
      </div>

      <base-button type="submit">Add Resource</base-button>
    </form>
  </wrapper>
</template>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>
