<script setup>
import ads from '../../data/ads.json'
</script>

<template>
  <template v-for="item in ads" :key="`${item.type}-${item.image}-${item.header}-${item.title}`">
    <div v-if="item.type === 'ad-card'" class="ad-card">
      <img :src="item.image" alt="Ad">
      <div class="ad-card-text">
        <p>{{ item.text }}</p>
        <button class="btn-outline">{{ item.buttonText }}</button>
      </div>
    </div>

    <div v-else-if="item.type === 'meetup-list'" class="meetup-card1">
      <strong class="meetup-header">{{ item.emoji }} {{ item.header }}</strong>

      <a v-for="meetup in item.items" :key="`${meetup.date}-${meetup.city}-${meetup.image}`" href="#">
        <img :src="meetup.image" :alt="meetup.city">
        <span class="meetup-text">
          {{ meetup.date }}: {{ meetup.city }}
          <span class="meetup-attribute">{{ meetup.rsvps }} RSVPs</span>

          <template v-if="meetup.avatars">
            <br>
            <img v-for="avatar in meetup.avatars" :key="avatar" :src="avatar" alt="user">
          </template>
        </span>
      </a>

      <button class="btn-outline1">{{ item.buttonText }}</button>
    </div>

    <div v-else-if="item.type === 'member-icons'" class="meetup-card2">
      <strong class="meetup-header">{{ item.emoji }} {{ item.header }}</strong>

      <div class="icon-row">
        <div v-for="icon in item.icons" :key="icon" class="icon-img">
          <img :src="icon" alt="member">
          <div class="hover-img">
            <img :src="icon" alt="member" class="blur">
            <div class="hover-text">
              <p>djcwencsnecoe</p>
              <p>ojdeowneoneojwnkbh</p>
            </div>
            <div class="normal-text">Hidden for non-members</div>
          </div>
        </div>
      </div>
    </div>

    <div v-else-if="item.type === 'suggestion-card'" class="card1">
      <img :src="item.image" :alt="item.city">
      <div class="card-rank">{{ item.rank }}</div>
      <span class="badge-top1">{{ item.badge }}</span>

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
          <span class="close-icon">✕</span>
        </div>

        <div class="rating-row">
          <span class="label">⭐ Overall</span>
          <div class="rating-bar"><div :class="['filling', item.ratings.overall]"></div></div>
        </div>
        <div class="rating-row">
          <span class="label">💵 Cost</span>
          <div class="rating-bar"><div :class="['filling', item.ratings.cost]"></div></div>
        </div>
        <div class="rating-row">
          <span class="label">📡 Internet</span>
          <div class="rating-bar"><div :class="['filling', item.ratings.internet]"></div></div>
        </div>
        <div class="rating-row">
          <span class="label">👍 Liked</span>
          <div class="rating-bar"><div :class="['filling', item.ratings.liked]"></div></div>
        </div>
        <div class="rating-row">
          <span class="label">👮 Safety</span>
          <div class="rating-bar"><div :class="['filling', item.ratings.safety]"></div></div>
        </div>
      </div>

      <div class="card-wifi">
        {{ item.wifi }}
        <span class="verify1">Mbps</span>
      </div>

      <div class="card-info">
        <h2>{{ item.city }}</h2>
        <p>{{ item.country }}</p>
      </div>

      <div class="card-stats">
        <span class="temperature">
          {{ item.weatherIcon }}
          <span class="above-temp1">
            Feels {{ item.feelsLike }}°
            <span class="temp-numbers1">{{ item.temp }}°</span>
          </span>
          <span v-if="item.weatherEmoji" class="emoji">{{ item.weatherEmoji }}</span>
        </span>

        <span class="price">
          ${{ item.price.toLocaleString() }} / mo
          <span class="verify">for a nomad</span>
        </span>
      </div>
    </div>

    <div v-else-if="item.type === 'featured-pick'" class="ad-card1">
      <span class="badge-top">{{ item.badgeTop }}</span>
      <img :src="item.image" alt="">
      <h2 class="main-title">{{ item.title }}</h2>
      <span class="badge-bottom">{{ item.badgeBottom }}</span>
    </div>

    <div v-else-if="item.type === 'telegram-join'" class="meetup-card3">
      <strong class="meetup-header">{{ item.emoji }} {{ item.header }}</strong>
      <div class="btn-telegram">
        <img :src="item.image" alt="telegram">
        <button class="btn-outline2">{{ item.buttonText }}</button>
      </div>
    </div>
  </template>
</template>
