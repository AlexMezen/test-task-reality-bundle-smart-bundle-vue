<template>
  <nav class="nav">
    <ul class="nav-links desktop-only">
      <li><a href="#">Home</a></li>
      <li><a href="#">Active investment</a></li>
      <li><a href="#">Fundraising</a></li>
      <li><a href="#">Smart Club</a></li>
      <li><a href="#">How It works</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
    
    <div class="logo">
      <img :src="logoImage" alt="Smart Bundles Logo">
    </div>
    
    <div class="mobile-menu mobile-only" @click="toggleMobileMenu">
      ☰
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

import logoImage from '@/assets/smartbundles_logo 2.png'

const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}
</script>

<style scoped>
.logo {
  font-weight: 900;
  font-size: 24px;
  color: rgba(19, 39, 96, 1);
}

.nav {
  background-color: white;
  padding: 10px 150px 10px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.nav-links {
  display: flex;
  gap: 30px;
  list-style: none;
}

.nav-links a {
  text-decoration: none;
  color: #666;
  font-size: 16px;
}

.nav-links a:hover {
  color: rgba(19, 39, 96, 1);
}

.mobile-menu {
  font-size: 24px;
  cursor: pointer;
  color: rgba(19, 39, 96, 1);
}

@media (max-width: 768px) {
  .nav {
    justify-content: space-between;
    padding: 15px;
  }

  .nav-links {
    display: none;
  }

  .mobile-menu {
    display: block;
  }
}
</style>

<style scoped>
.logo {
  font-weight: 900;
  font-size: 24px;
  color: rgba(19, 39, 96, 1);
}

.nav {
  background-color: white;
  padding: 10px 150px 10px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
}

.nav-links {
  display: flex;
  gap: 30px;
  list-style: none;
}

.nav-links a {
  text-decoration: none;
  color: #666;
  font-size: 16px;
}

.nav-links a:hover {
  color: rgba(19, 39, 96, 1);
}

.mobile-menu {
  font-size: 24px;
  cursor: pointer;
  color: rgba(19, 39, 96, 1);
}

@media (max-width: 768px) {
  .nav {
    justify-content: space-between;
    padding: 15px;
  }

  .nav-links {
    display: none;
  }

  .mobile-menu {
    display: block;
  }
}
</style>