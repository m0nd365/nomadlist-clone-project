<script setup>
import { ref } from 'vue'
import footer from '../../data/footer.json'

const showFooter = ref(true)
</script>

<template>
  <div v-if="showFooter === true" class="footer-stick">
    {{ footer.footerSticky.message }}

    <div class="btn-white">
      <a href="#">{{ footer.footerSticky.button.text }}</a>
    </div>

    <span class="delete" @click="showFooter = false">
      {{ footer.footerSticky.closeIcon }}
    </span>
  </div>
</template>
