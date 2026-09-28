<script setup>
import { ref } from 'vue'
import logoSearch from '../../data/logo_search.json'
import searchBar from '../../data/search_bar.json'
import sortBy from '../../data/sort_by.json'

defineProps({
  filtersOpen: {
    type: Boolean,
    default: false,
  },
})

defineEmits(['toggle-filters'])

const compareOpen = ref(false)
</script>

<template>
  <div class="view-contents">
    <div class="filters-bar">
      <div class="mini-map tooltip" tabindex="0" data-tooltip="Click to open nav">
        <svg class="logo" enable-background="new 0 0 907.3 906.4" viewBox="0 0 907.3 906.4" xmlns="http://www.w3.org/2000/svg">
          <path d="m0 463.4c0-7.3 0-14.7 0-22 .4-2.9 1-5.9 1.1-8.8.8-27 4.2-53.7 10.5-79.9 32.6-134.6 109.7-235.2 231.3-301.2 54-29.4 112.1-45.8 173.3-50.5 22.7-1.7 45.6-.9 68.4-.3 24.3.6 48.3 4.7 71.9 10.4 105.4 25.4 191.6 80.9 257.7 166.7 56.2 73.1 86.5 156.2 92.3 248.1 1.7 27.2.9 54.5-2.6 81.7-3 23.4-7.4 46.5-13.9 69.1-25.5 88.5-73.3 162.9-143.7 222.1-78.8 66.3-169.9 101.8-272.9 106.3-2.4.1-4.9.7-7.3 1.1-8 0-16 0-24 0-2.3-.4-4.5-1-6.8-1.1-31.9-.9-63.2-5.6-94-13.6-149.4-38.5-267.8-148.7-317.2-294.7-13.7-40.6-21.5-82.2-23-125.1-.1-2.8-.7-5.5-1.1-8.3zm235.6 29v200c0 11.1 5.7 19.3 16.3 22.3 11.8 3.3 22.6.3 32.5-6.8 33.6-24 67.3-47.8 100.9-71.9 3.5-2.5 5.8-2.7 9.5-.2 36.6 25 73.4 49.6 110.1 74.5 6.8 4.6 14.3 7.2 22.1 4.9 6.9-2 14-4.8 19.8-8.8 24.4-16.8 48.4-34.2 72.6-51.4 14.8-10.5 29.6-21 44.2-31.8 7.4-5.5 10.8-12.9 10.8-22.4-.1-132.8-.1-265.6-.1-398.4 0-11.1-5.9-19.2-16.6-22.1-11.9-3.2-22.6-.1-32.5 6.9-33.4 23.8-66.8 47.5-100.1 71.3-3.3 2.4-5.6 2.6-9.1.2-35.4-24.1-70.9-48-106.4-71.9-16-10.8-30.9-10.6-46.7.6-14.4 10.2-28.8 20.5-43.2 30.7-23.1 16.4-46.1 32.8-69.2 49.2-10 7.1-15.2 16.2-15.1 29.1.4 65.3.2 130.6.2 196z" fill="var(--brand-color)"></path>
          <path d="m235.6 492.4c0-65.3.2-130.6-.2-196-.1-12.8 5.1-22 15.1-29.1 23.1-16.4 46.1-32.8 69.2-49.2 14.4-10.2 28.7-20.5 43.2-30.7 15.8-11.2 30.8-11.4 46.7-.6 35.5 23.9 71 47.8 106.4 71.9 3.5 2.4 5.8 2.2 9.1-.2 33.3-23.9 66.7-47.6 100.1-71.3 9.9-7 20.6-10.2 32.5-6.9 10.7 2.9 16.6 11 16.6 22.1 0 132.8 0 265.6.1 398.4 0 9.5-3.4 16.9-10.8 22.4-14.6 10.8-29.4 21.3-44.2 31.8-24.1 17.2-48.1 34.6-72.6 51.4-5.9 4-12.9 6.8-19.8 8.8-7.9 2.3-15.3-.3-22.1-4.9-36.7-24.9-73.5-49.5-110.1-74.5-3.7-2.5-6-2.3-9.5.2-33.6 24.1-67.3 48-100.9 71.9-9.9 7-20.7 10.1-32.5 6.8-10.7-3-16.3-11.2-16.3-22.3 0-66.7 0-133.4 0-200zm285.8 165.9c.1-2.4.2-3.7.2-4.9 0-108 0-216 .1-324 0-3-.9-4.9-3.4-6.6-41.6-28-83.2-56-124.7-84-.9-.6-1.9-.8-3.2-1.4v3c0 108.5 0 217-.1 325.5 0 3.4 1.4 5 4 6.7 33.2 22.3 66.3 44.7 99.4 67 8.9 6.1 17.9 12.1 27.7 18.7z" fill-opacity="0" fill="#000"></path>
          <path d="m521.4 658.3c-9.8-6.6-18.8-12.6-27.7-18.7-33.1-22.4-66.3-44.7-99.4-67-2.5-1.7-4-3.3-4-6.7.1-108.5.1-217 .1-325.5 0-.8 0-1.6 0-3 1.3.6 2.4.9 3.2 1.4 41.6 28 83.1 56.1 124.7 84 2.5 1.7 3.4 3.6 3.4 6.6-.1 108-.1 216-.1 324 0 1.3-.1 2.6-.2 4.9z" fill="var(--brand-color)"></path>
        </svg>
        <span class="sign-down">
          <img src="/images/chevron-down.svg" alt="chevron-down">
        </span>

        <div class="logo-dropdown-bar" id="dropdown">
          <a v-for="link in logoSearch.topLinks" :key="link.text" href="#">{{ link.text }}</a>

          <template v-for="section in logoSearch.sections" :key="section.title">
            <div class="menu-section full-width">
              <span class="section-title">{{ section.title }}</span>
            </div>

            <div v-for="(column, columnIndex) in section.columns" :key="`${section.title}-${columnIndex}`" class="menu-column">
              <a v-for="item in column" :key="item.text" href="#">
                <img v-if="item.img" :src="item.img" :alt="item.text">
                {{ item.text }}
                <span v-if="item.badge" class="badge">{{ item.badge }}</span>
              </a>
            </div>
          </template>
        </div>
      </div>

      <div class="filters-btn" id="filters-toggle" @click="$emit('toggle-filters')">
        <span v-if="filtersOpen === true">Close filters</span>
        <span v-else>Filters</span>
      </div>

      <div class="filters-search" tabindex="0">
        <input id="search" type="text" class="input-filters" placeholder="Search or filter..." tabindex="0">
        <div class="filters-circle" id="circle">
          <img src="/images/plus.svg" alt="plus">
        </div>
        <div class="search-filters">
          <div v-for="(column, index) in searchBar.columns" :key="index" class="search-column">
            <div v-for="item in column.items" :key="item.text" class="att" :class="{ tooltip: Boolean(item.tooltip) }" :data-tooltip="item.tooltip">
              <span>{{ item.text }}</span>
            </div>
          </div>
        </div>
      </div>

      <div class="main">
        <div class="filters-compare" :class="{ 'compare-active': compareOpen === true }" @click="compareOpen = !compareOpen">
          <span v-if="compareOpen === true">Exit compare</span>
          <span v-else>Compare</span>
        </div>
        <div class="score1 tooltip" data-tooltip="Sort results by any attribute you like">
          <select class="score filters-grid">
            <option value="Nomad Score">Grid view</option>
            <option value="Nomad Score">Map view</option>
            <option value="Nomad Score">Chart view</option>
          </select>
        </div>

        <div class="score tooltip" :data-tooltip="sortBy.tooltip">
          <select class="score filters-compare1">
            <option v-for="option in sortBy.options" :key="option" :value="option">
              {{ option }}
            </option>
          </select>
        </div>

        <div class="side-down-behind tooltip" data-tooltip="Sorting highest first (desc)">
          <img src="/images/chevron-down.svg" alt="chevron-down">
        </div>

        <span class="btn-red1">Join Nomads.com →</span><br>
      </div>
    </div>

    <div class="city-compare" :class="{ active: compareOpen === true }">
      City compare
    </div>
  </div>
</template>
