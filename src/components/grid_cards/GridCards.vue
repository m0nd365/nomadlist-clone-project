<script setup>
import cards from '../../data/grid_cards.json'

const ratingRows = [
  { key: 'overall', label: '⭐ Overall' },
  { key: 'cost', label: '💵 Cost' },
  { key: 'internet', label: '📡 Internet' },
  { key: 'liked', label: '👍 Liked' },
  { key: 'safety', label: '👮 Safety' },
]
</script>

<template>
  <div v-for="card in cards" :key="card.rank" class="card">
    <img :src="card.image" :alt="card.city">

    <span v-if="card.isPopular === true" class="badge-top">Popular</span>
    <div class="card-rank">{{ card.rank }}</div>

    <span class="wifi-beside">
      <svg width="25" class="wifi-svg" aria-hidden="true" data-prefix="fas" data-icon="wifi" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512">
        <path fill="currentColor" d="M634.91 154.88C457.74-8.99 182.19-8.93 5.09 154.88c-6.66 6.16-6.79 16.59-.35 22.98l34.24 33.97c6.14 6.1 16.02 6.23 22.4.38 145.92-133.68 371.3-133.71 517.25 0 6.38 5.85 16.26 5.71 22.4-.38l34.24-33.97c6.43-6.39 6.3-16.82-.36-22.98zM320 352c-35.35 0-64 28.65-64 64s28.65 64 64 64 64-28.65 64-64-28.65-64-64-64zm202.67-83.59c-115.26-101.93-290.21-101.82-405.34 0-6.9 6.1-7.12 16.69-.57 23.15l34.44 33.99c6 5.92 15.66 6.32 22.05.8 83.95-72.57 209.74-72.41 293.49 0 6.39 5.52 16.05 5.13 22.05-.8l34.44-33.99c6.56-6.46 6.33-17.06-.56-23.15z"></path>
      </svg>
    </span>

    <div class="action-hover">
      <div class="hover-header">
        <svg class="hover-heart" aria-hidden="true" width="25" focusable="false" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512">
          <path fill="none" stroke="white" stroke-width="30" d="M462.3 62.6C407.5 15.9 326 24.3 275.7 76.2L256 96.5l-19.7-20.3C186.1 24.3 104.5 15.9 49.7 62.6c-62.8 53.6-66.1 149.8-9.9 207.9l193.5 199.8c12.5 12.9 32.8 12.9 45.3 0l193.5-199.8c56.3-58.1 53-154.3-9.8-207.9z"></path>
        </svg>
        <span class="close-icon tooltip" data-tooltip="Hide this...">✕</span>
      </div>

      <div v-for="row in ratingRows" :key="row.key" class="rating-row">
        <span class="label">{{ row.label }}</span>
        <div class="rating-bar">
          <div class="filling" :class="card.ratings[row.key]"></div>
        </div>
      </div>
    </div>

    <div class="card-wifi">
      {{ card.wifi }}
      <span class="verify1">Mbps</span>
    </div>

    <div class="card-info">
      <h2>{{ card.city }}</h2>
      <p>{{ card.country }}</p>
    </div>

    <div class="card-stats">
      <span v-if="card.temp > 10" class="temperature1">
        {{ card.weatherIcon }}
        <span v-if="card.temp > 30" class="above-temp1">
          Feels {{ card.feelsLike }}°
          <span class="temp-numbers1">{{ card.temp }}°</span>
        </span>
        <span v-else class="above-temp">
          Feels {{ card.feelsLike }}°
          <span class="temp-numbers1">{{ card.temp }}°</span>
        </span>

        <span v-if="card.weatherEmoji" class="emoji">{{ card.weatherEmoji }}</span>

        <span v-if="card.aqi !== null && card.aqi > 100" class="about1">
          AQI
          <span>{{ card.aqi }}</span>
        </span>
        <span v-else-if="card.aqi !== null && card.aqi <= 100" class="about">
          AQI
          <span>{{ card.aqi }}</span>
        </span>
      </span>

      <span v-else class="temperature">
        {{ card.weatherIcon }}
        <span class="above-temp">
          Feels {{ card.feelsLike }}°
          <span class="temp-numbers1">{{ card.temp }}°</span>
        </span>

        <span v-if="card.weatherEmoji !== null" class="emoji">{{ card.weatherEmoji }}</span>

        <span v-if="card.aqi !== null && card.aqi > 100" class="about1">
          AQI
          <span>{{ card.aqi }}</span>
        </span>
        <span v-else-if="card.aqi !== null && card.aqi <= 100" class="about">
          AQI
          <span>{{ card.aqi }}</span>
        </span>
      </span>

      <span class="price">
        ${{ card.price.toLocaleString() }} / mo
        <span class="verify">for a nomad</span>
      </span>
    </div>
  </div>
</template>
