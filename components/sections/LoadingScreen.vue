<template>
  <div v-if="loading" class="loading-page">
    <div class="loading"></div>
  </div>
</template>
<script>
  import { gsap } from "gsap";
  export default {
    data: () => ({
      loading: false,
    }),
    created() {
      this.$nuxt.$on('loading-animation', () => gsap.to('.loading-page', {opacity:0, duration:0.5, ease: 'power4.easeOut'}))
    },
    methods: {
      start() {
        this.loading = true
      },
      finish() {
        this.loading = false
      },
    },
  }
</script>
<style scoped>
  .loading-page {
    position: fixed;
    top: 0;
    right: 0;
    z-index: 1000;
    padding: 1rem;
    text-align: center;
    font-family: sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    width: 100vw;
    height: 100vh;
    background-color: black;
  }
  .loading {
    display: inline-block;
    width: 3rem;
    height: 3rem;
    border: 4px solid rgba(150, 150, 255, 1);
    border-radius: 50%;
    border-top-color: rgba(200, 200, 255, 1);
    animation: spin 1s ease-in-out infinite;
  }
  @keyframes spin {
    to {
      -webkit-transform: rotate(360deg);
    }
  }
</style>