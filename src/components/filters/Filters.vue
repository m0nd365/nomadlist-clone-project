<script setup>
import filtersData from '../../data/filters.json'

const filters = filtersData.filters
</script>

<template>
  <div class="filters-header">
    <label class="filters-label">What</label>
  </div>

  <div class="filter-grid">
    <div v-for="item in filters.what.temperature" :key="item.label" class="filter-item tooltip" :data-tooltip="item.tooltip">
      {{ item.label }}
    </div>
  </div>

  <div class="filter-grid">
    <div v-for="item in filters.what.budget" :key="item" class="filter-item">
      {{ item }}
    </div>
  </div>

  <div class="filter-grid1">
    <span v-for="item in filters.what.attributes.slice(0, 2)" :key="item" class="filter-item">{{ item }}</span>
  </div>
  <div class="filter-grid1">
    <span v-for="item in filters.what.attributes.slice(2, 4)" :key="item" class="filter-item">{{ item }}</span>
  </div>
  <div class="filter-grid1">
    <span v-for="item in filters.what.attributes.slice(4, 6)" :key="item" class="filter-item">{{ item }}</span>
  </div>
  <div class="filter-grid2">
    <div v-for="item in filters.what.attributes.slice(6, 8)" :key="item" class="filter-item">{{ item }}</div>
  </div>
  <div class="filter-grid1">
    <span v-for="item in filters.what.attributes.slice(8, 10)" :key="item" class="filter-item">{{ item }}</span>
  </div>
  <div class="filter-grid3">
    <span class="filter-item">{{ filters.what.attributes[10] }}</span>
  </div>

  <div class="filters-header">
    <label class="filters-label">Where</label>
  </div>

  <div class="filter-grid4">
    <div v-for="item in filters.where.continents" :key="item" class="filter-item1">
      {{ item }}
    </div>
  </div>

  <div class="filter-grid1">
    <span v-for="item in filters.where.regionSocial.slice(0, 2)" :key="item" class="filter-item">{{ item }}</span>
  </div>
  <div class="filter-grid1">
    <span v-for="item in filters.where.regionSocial.slice(2, 4)" :key="item" class="filter-item">{{ item }}</span>
  </div>
  <div class="filter-grid1">
    <span v-for="item in filters.where.regionSocial.slice(4, 6)" :key="item" class="filter-item">{{ item }}</span>
  </div>

  <div class="filters-header">
    <label class="filters-label">When</label>
  </div>

  <div class="filter-grid2">
    <div v-for="item in filters.when.frequency" :key="item" class="filter-item">
      {{ item }}
    </div>
  </div>

  <div class="filter-grid6">
    <div v-for="month in filters.when.months" :key="month" class="filter-item1">
      {{ month }}
    </div>
  </div>

  <div class="filters-header">
    <label class="filters-label">Reviewed by members</label>
  </div>

  <div class="filter-grid1">
    <span v-for="item in filters.reviewMembers.slice(0, 2)" :key="item.label" class="filter-item">
      {{ item.label }} ({{ item.rating }})
    </span>
  </div>
  <div class="filter-grid1">
    <span v-for="item in filters.reviewMembers.slice(2, 4)" :key="item.label" class="filter-item">
      {{ item.label }} ({{ item.rating }})
    </span>
  </div>
</template>

