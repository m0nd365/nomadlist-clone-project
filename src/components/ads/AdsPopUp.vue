<script setup>
import { ref } from 'vue'
import adsPopupData from '../../data/ads-popup.json'

const popup = adsPopupData.adsPopup
const benefits = popup.content.filter((item) => item.type === 'benefit')
const testimonials = popup.content.filter((item) => item.type === 'testimonial')
const showPopup = ref(true)
</script>

<template>
  <div v-if="showPopup === true" class="wrap">
    <div class="modal-overlay" @click.self="showPopup = false">
      <div class="modal-box">
        <div class="top-section">
          <div class="left-col">
            <div class="rating-star">
              <div class="star">
                <img v-for="star in popup.ratingInfo.stars" :key="star" src="/images/emoji-star.png" alt="emoji-star">
              </div>
              <p>
                Customer rating
                <strong>{{ popup.ratingInfo.score }}</strong>|
                <strong>{{ popup.ratingInfo.reviews.toLocaleString() }}</strong>
                reviews
              </p>
            </div>

            <div class="item-list">
              <template v-for="benefit in benefits" :key="benefit.linkText">
                <div class="text-wrap">
                  <a href="#">✅ {{ benefit.linkText }}</a>
                  {{ benefit.desc }}
                </div>
                <div class="map-placeholder">
                  <img :src="benefit.image" :alt="benefit.linkText">
                </div>
              </template>
            </div>
          </div>

          <div class="right-col">
            <div class="video-placeholder">
              <img :src="popup.signupSection.videoThumbnail" alt="thumbnail">
              <svg class="play-icon" xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="currentColor" viewBox="0 0 24 24">
                <path d="M12 2C6.49 2 2 6.49 2 12s4.49 10 10 10 10-4.49 10-10S17.51 2 12 2m0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8"></path>
                <path d="m9 17 8-5-8-5z"></path>
              </svg>
            </div>

            <div class="num-btn">
              <span>{{ popup.signupSection.membershipStats }}</span>
            </div>

            <input type="email" class="input-email" :placeholder="popup.signupSection.placeholder">

            <select class="input-select">
              <option v-for="gender in popup.signupSection.genders" :key="gender">
                {{ gender }}
              </option>
            </select>

            <button class="join-btn">{{ popup.signupSection.buttonText }}</button>
          </div>
        </div>

        <div class="people-footer">
          <div v-for="testimonial in testimonials" :key="testimonial.user" class="people-footer-list">
            <img :src="testimonial.avatar" :alt="testimonial.user">
            <strong>{{ testimonial.user }}</strong>
            : "{{ testimonial.quote }}"
          </div>
        </div>

        <div class="last-footer">
          <p class="last-footer-text">{{ popup.footerText }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
