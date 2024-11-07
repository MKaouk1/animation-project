import Image from '@/components/Image.vue';
<template>
  <div class="container">
  <v-app-bar>
    <v-app-bar-title class="logo">
      <img
        src="../assets/Olympus-Shield-logo-white.avif"
        alt="Logo"
        height="100px"
      />
    </v-app-bar-title>
    <v-spacer></v-spacer>
    <div v-if="!isMobile">
    <v-btn v-for="link in links" :key="link.name" text>
      <router-link :to="link.route" class="links">{{ link.name }}</router-link>
    </v-btn>
  </div>
  <v-btn icon @click="toggleDrawer" v-if="isMobile" class="hamburger-btn">
        <div class="hamburger-icon">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </v-btn>

    <v-navigation-drawer v-if="drawer" v-model="drawer" app temporary>
      <v-list>
        <v-list-item v-for="link in links" :key="link.name" @click="navigate(link.route)">
          <v-list-item-title>{{ link.name }}</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

  </v-app-bar>
</div>
</template>

<script>
import { ref,computed } from 'vue';
import { useRouter } from 'vue-router';
import { useDisplay } from 'vuetify/lib/framework.mjs';
export default{
  name:'Nav',
  setup(){
const router = useRouter();

const { xs } = useDisplay();
const isMobile = computed(() => xs.value);
const drawer = ref(false);
const links = [
  { name: 'Home', route: '/' },
  { name: 'Services', route: '/services' },
  { name: 'Customers', route: '/customers' },
  { name: 'Pricing', route: '/pricing' },
  { name: 'About', route: '/about' },
];


const toggleDrawer = () => {
  drawer.value = !drawer.value;
};

const navigate = (route) => {
  router.push(route);
  drawer.value = false; 
}
return{
  links,
  toggleDrawer,
  navigate,
  drawer,
  isMobile
}
}
}
</script>

<style scoped>
.container{
  background: linear-gradient(to bottom, red, black);

}
.links{
  text-decoration: none;
  color:black;
}

.hamburger-btn {
  border: 1px solid white;
  border-radius: 5px;   
  padding: 4px;         
}

.hamburger-icon {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 16px; /* Total height for the 3 lines */
}

.hamburger-icon span {
  display: block;
  width: 20px;
  height: 2px;
  background-color: white;
}
</style>
