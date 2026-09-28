<script setup>
import headerInfo from '../../data/header_info.json'
</script>

<template>
  <div class="header-text">
    <div class="community-logo">
      <span class="community-text">{{ headerInfo.communityInfo.text }}</span>

      <span class="community-star">
        <img v-for="star in headerInfo.communityInfo.stars" :key="star" src="/images/star.svg" alt="star">
      </span>

      <span class="community-since">{{ headerInfo.communityInfo.since }}</span>
      <img :src="headerInfo.communityInfo.wing" alt="wing">
    </div>

    <h1>{{ headerInfo.mainHeading }}</h1>

    <div class="report-benefits">
      <span class="sub-text">{{ headerInfo.subText }}</span>
      <br>
      <br>

      <div class="people">
        <div v-for="person in headerInfo.people" :key="person" class="people-icons">
          <img :src="person" alt="" class="people-scale">
        </div>
      </div>

      <div v-for="benefit in headerInfo.benefits" :key="benefit.text" class="benefits">
        {{ benefit.emoji }}
        <a href="#">{{ benefit.text }}</a>
        {{ benefit.sub }}
      </div>
    </div>
  </div>

  <div class="header-sign-up">
    <div class="intro-vdo">
      <img :src="headerInfo.metadata.video_thumbnail" alt="thumbnail">
      <svg class="play-icon" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 24 24">
        <!--Boxicons v3.0.8 https://boxicons.com | License  https://docs.boxicons.com/free-->
        <path d="M12 2C6.49 2 2 6.49 2 12s4.49 10 10 10 10-4.49 10-10S17.51 2 12 2m0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8"></path>
        <path d="m9 17 8-5-8-5z"></path>
      </svg>
    </div>
    <br>
    <p>
      <input type="email" class="email" placeholder="Type your email...">
    </p>
    <br>
    <span class="btn-red">Join {{ headerInfo.source }} →</span><br>
    <p v-if="headerInfo.action === 'login_or_signup'" class="mini-text">
      If you already have an account, we'll log you in
    </p>
  </div>
</template>
