<script>
import store from '../../utils/utils';

import Wrapper from '../wrapper/Wrapper.vue';
import BaseButton from '../button/Button.vue';

import AddResource from './AddResource.vue';
import StoreResource from './StoreResource.vue';
import { KeepAlive } from 'vue';

export default {
  components: { Wrapper, BaseButton, AddResource, StoreResource, KeepAlive },

  data() {
    return {
      selectedTab: 'store-resource',

      store: store,
    };
  },

  computed: {
    storeButtonMode() {
      return this.selectedTab === 'store-resource' ? null : 'flat';
    },

    addButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },

  provide() {
    return {
      resource: this.store,
      addResource: this.addResource,
      removeResource: this.removeResource,
    };
  },

  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },

    addResource(title, description, url) {
      const newResource = {
        id: new Date().toString(),
        title: title,
        description: description,
        link: url,
      };

      this.store.unshift(newResource);
      this.selectedTab = 'store-resource';
    },

    removeResource(id) {
      const resIndex = this.store.findIndex((res) => res.id !== id);
      this.store.splice(resIndex, 1);
    },
  },
};
</script>

<template>
  <wrapper>
    <base-button
      :mode="storeButtonMode"
      @click="setSelectedTab('store-resource')"
      >Store Resourse</base-button
    >

    <base-button :mode="addButtonMode" @click="setSelectedTab('add-resource')"
      >Add Resourse</base-button
    >

    <keep-alive>
      <component :is="selectedTab" />
    </keep-alive>
  </wrapper>
</template>
