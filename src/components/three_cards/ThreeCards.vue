<script setup>
import threeCards from '../../data/three_cards.json'
</script>

<template>
  <div v-for="(card, index) in threeCards" :key="card.title" :class="`three-boxes-${index + 1}`">
    <p>
      "{{ card.title }}"
    </p>
    <img :src="card.image" :alt="card.alt">
  </div>
</template>
