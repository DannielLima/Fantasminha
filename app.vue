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
      meta: [
        { name: 'description', content: 'Um app com pegadinha, tenha cuidado ao usar!' },
        { name: 'keywords', content: 'jumpscare, susto, pegadinha, Nuxt, Vue, Typescript' },
        { name: 'author', content: 'Seu Nome' },
        { name: 'robots', content: 'index, follow' },
      ]
    });
  }
});
</script>
