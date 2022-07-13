<template>
<div class="sections-container">
  <Section1/>
  <Section2/>
</div>
</template>

<script>
export default {
  mounted() {
    this.$nextTick(() => {
      this.$nuxt.$loading.start()
      setTimeout(() => this.$nuxt.$loading.finish(), 4000)
    })
  }
}
</script>
