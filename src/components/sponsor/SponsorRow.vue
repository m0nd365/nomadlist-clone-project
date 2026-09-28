<script setup>
import sponsorRow from '../../data/sponsor_row.json'
</script>

<template>
  <p>
    as seen on
    <img v-for="sponsor in sponsorRow" :key="sponsor.alt" :src="sponsor.image" :alt="sponsor.alt">
  </p>
</template>
