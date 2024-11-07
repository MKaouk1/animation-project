<template>
  <div
    class="icon-card"
    @mouseover="isHovered = true"
    @mouseleave="isHovered = false"
  >
    <div class="contained">
      <div class="icon-container">
        <div
          :class="{ spinForward: isHovered, spinReverse: !isHovered }"
          class="icon-wrapper"
        >
          <slot name="icon" :isHovered="isHovered"></slot>
        </div>
        <h5 class="icon-title">{{ title }}</h5>
      </div>
      <p class="icon-description">{{ description }}</p>
    </div>
  </div>
</template>

<script>
import SVG from "./SVG.vue";
import { ref } from "vue";
export default {
  name: "IconCard",
  components: {
    SVG,
  },
  props: {
    title: {
      type: String,
      required: true,
    },
    description: {
      type: String,
      required: true,
    },
  },
  setup(){
 const isHovered = ref(false);
  return{
    isHovered
  }
  }
};
</script>

<style>
.icon-card {
  background: black;
  color: white;
}
.icon-container {
  display: flex;
}

.contained {
  padding: 10%;
}
.icon-title {
  font-size: 1.25rem;
  margin-top: auto;
}
.icon-card:hover svg {
  fill: red;
}

.icon-wrapper {
  transition: transform 0.5s;
}

.spinForward {
  animation: spinForward 0.4s linear forwards;
}

.spinReverse {
  animation: spinReverse 0.4s linear forwards;
}

@keyframes spinForward {
  0% {
    transform: rotateY(0deg);
  }
  100% {
    transform: rotateY(360deg) scale(1.1, 1.1);
  }
}

@keyframes spinReverse {
  0% {
    transform: rotateY(360deg);
  }
  100% {
    transform: rotateY(0deg) scale(1, 1);
  }
}
</style>
