<template>
    <div>
      <Nav></Nav>
      <Image />
      <div class="icon-cards-wrapper">
        <div class="icon-container">
            <IconCard
        :title="'Penetration Testing'"
        :description="'The Art Of Using Offensive Skills To Detect Cyber Vulnerabilities And Weaknesses.'"
      >
        
        <template #icon>
          <SVG></SVG>
        </template>
      </IconCard>
    </div>
      </div>
    </div>
  </template>
  
  <script>
  import Image from '@/components/Image.vue';
  import Nav from '@/components/Nav.vue';
  import IconCard from '@/components/IconCard.vue';
  import SVG from '@/components/SVG.vue';
  export default {
    name: 'HomeView',
    components: {
      Image,
      Nav,
      IconCard,
      SVG
    },
  };
  </script>
  <style scoped>
  .icon-cards-wrapper {
    display: flex;
    flex-direction: row;
    padding: 10%;
  }
  
  .icon-container {
    transition: transform 0.3s ease;
    
  }
  
  
  .icon-container:hover {
    transform: translateY(-10px);
  }
  body, html, .container {
  margin: 0;
  padding: 0;
}
</style>