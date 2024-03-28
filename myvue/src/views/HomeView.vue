<template>
  <MainPage />
</template>

<script>
import { defineComponent } from 'vue';

// Components
import MainPage from '../components/MainPage.vue';

export default defineComponent({
  name: 'HomeView',

  components: {
    MainPage,
  },
});
</script>