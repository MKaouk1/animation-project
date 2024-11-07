<template>
    <div class="image-container">
        <h1>Multi-Certified For The Most Advanced Offensive Cyber Security.</h1>
        
    </div>
</template>
<script>
export default {
    name:'Image',
    setup(){

    }
}
</script>
<style scoped>
.image-container {
  background-image: url('../assets/cybersecurity-awareness-month-2020\ \(1\).avif');
  background-size: 100% 100%; 
  background-repeat: no-repeat;
  height: 20em; 
  width: 100%;
  animation: moveBackgroundUp 15s infinite linear;
  overflow: hidden;
  position: relative;
}

@keyframes moveBackgroundUp {
    0% {
    background-size: 100% 100%; 
  }
  50% {
    background-size: 100% 130%; 
  }
  100% {
    background-size: 100% 100%; 
  }
}

h1{
    color: white;
    padding-left:6% ;
    max-width: 35%;
    font-size: 2.25rem;
}
</style>