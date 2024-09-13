<template>
  <div>
    <Jumpscare />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import { useHead } from '@vueuse/head';
import Jumpscare from '~/components/Jumpscare.vue';

export default defineComponent({
  components: {
    Jumpscare
  },
  setup() {
    useHead({
      title: 'Formulário',
    });
  }
});
</script>
