<script setup>
import { nextTick, onMounted, ref } from 'vue'
import Ads from '../grid_cards/Ads.vue'
import AdsPopUp from '../ads/AdsPopUp.vue'
import Filters from '../filters/Filters.vue'
import Footer from '../footer/Footer.vue'
import GridCards from '../grid_cards/GridCards.vue'
import Header from '../header/Header.vue'
import Navbar from '../navbar/Navbar.vue'
import SponsorRow from '../sponsor/SponsorRow.vue'
import ThreeCards from '../three_cards/ThreeCards.vue'

// Always start at the top on refresh instead of restoring the previous scroll position
if ('scrollRestoration' in history) {
  history.scrollRestoration = 'manual'
}

onMounted(() => {
  window.scrollTo(0, 0)
})

const filtersOpen = ref(false)
// Once filters are opened, the top screen stays hidden until the page is refreshed
const topScreenHidden = ref(false)

async function toggleFilters() {
  filtersOpen.value = !filtersOpen.value
  topScreenHidden.value = true

  if (filtersOpen.value === true) {
    await nextTick()
    window.scrollTo(0, 0)
  }
}
</script>

<template>
  <!-- Top Screen -->
  <div v-show="topScreenHidden === false" class="main-top-screen" id="main-top">
    <video autoplay muted loop playsinline>
      <source src="/images/nomad-vdo-hd.mp4" type="video/mp4">
    </video>
    <div class="video-overlay"></div>

    <div class="top-screen-container">
      <Header/>
    </div>

    <svg viewBox="0 0 1440 120" class="wave" data-label="svg.wave">
      <path d="M1440,21.2101911 L1440,120 L0,120 L0,21.2101911 C120,35.0700637 240,42 360,42 C480,42 600,35.0700637 720,21.2101911 C808.32779,12.416393 874.573633,6.87702029 918.737528,4.59207306 C972.491685,1.8109458 1026.24584,0.420382166 1080,0.420382166 C1200,0.420382166 1320,7.35031847 1440,21.2101911 Z"></path>
    </svg>

    <div class="new-screen">
      <SponsorRow/>
    </div>

  </div>
  <!-- //Top Screen -->


  <!-- Whole Wrapper -->
  <div class="big-container-wrapper" :class="{ 'filters-open': filtersOpen === true }">
    <!-- Left Filters -->
    <div class="left" id="left-js">
      <div class="filters">
        <Filters/>
      </div>
    </div>
    <!-- //Left Filters -->


    <!-- Right Filters -->
    <div class="right" id="right-side">
      <div class="three-boxes">
        <ThreeCards/>
      </div>

      <Navbar :filters-open="filtersOpen" @toggle-filters="toggleFilters"/>


      <!-- Grid Body -->
      <div class="main-grid" id="main-id" :class="{ 'filters-active': filtersOpen === true }">
        <div class="grid-cards">
          <GridCards/>
        </div>

        <!-- Side Bar  -->
        <div class="grid-ads">
          <Ads/>
        </div>
        <!-- //Side Bar -->

      </div>
      <!-- //Grid Body -->
    </div>
  </div>
  <!-- //Right Filters -->
  <!-- //Whole Wrapper -->

  <AdsPopUp/>
  <Footer/>
</template>
