<template>
  <nav class="p-5 bg-green-400 text-white mb-10">
    <router-link :to="{ name: 'Home' }">Snazzy Fake Blog</router-link>
  </nav>
  <div class="container">
    <router-view></router-view>
    <div v-if="isLoading">
      <div class="spcontainers">
        <div class="spinner">
          <div></div>
          <div></div>
          <div></div>
          <div></div>
          <div></div>
          <div></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import usePageRequests from "./composables/usePageRequests";
const { isLoading } = usePageRequests();
</script>
<style lang="css" scoped>
.container {
  max-width: 960px;
  margin: 0 auto;
  position: relative;
}

.spcontainers {
  width: 100%;
  height: 100vh;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%);
  display: flex;
  justify-content: center;
  align-items: center;
}

.spinner {
  width: 32px;
  height: 32px;
  animation: spinner-y0fdc1 2s infinite ease;
  transform-style: preserve-3d;
}

.spinner > div {
  background-color: rgba(7, 217, 171, 0.2);
  height: 100%;
  position: absolute;
  width: 100%;
  border: 1.6px solid rgba(7, 217, 171, 0.91);
}

.spinner div:nth-of-type(1) {
  transform: translateZ(-16px) rotateY(180deg);
}

.spinner div:nth-of-type(2) {
  transform: rotateY(-270deg) translateX(50%);
  transform-origin: top right;
}

.spinner div:nth-of-type(3) {
  transform: rotateY(270deg) translateX(-50%);
  transform-origin: center left;
}

.spinner div:nth-of-type(4) {
  transform: rotateX(90deg) translateY(-50%);
  transform-origin: top center;
}

.spinner div:nth-of-type(5) {
  transform: rotateX(-90deg) translateY(50%);
  transform-origin: bottom center;
}

.spinner div:nth-of-type(6) {
  transform: translateZ(16px);
}

@keyframes spinner-y0fdc1 {
  0% {
    transform: rotate(45deg) rotateX(-25deg) rotateY(25deg);
  }

  50% {
    transform: rotate(45deg) rotateX(-385deg) rotateY(25deg);
  }

  100% {
    transform: rotate(45deg) rotateX(-385deg) rotateY(385deg);
  }
}
</style>
