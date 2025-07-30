<template>
  <div id="app">
    <HeaderComponent class="desktop-only" />
    <NavigationComponent />
    <main class="main-content">
      <MobileHeader class="mobile-only" />
      <ProfileComponent />
      <div class="plus-icon desktop-only">
        <div class="plus-btn">+</div>
      </div>
      <AuthSection />
      <LeaderSection />
    </main>
  </div>
</template>

<script setup>
import HeaderComponent from './components/HeaderComponent.vue'
import NavigationComponent from './components/NavigationComponent.vue'
import MobileHeader from './components/MobileHeader.vue'
import ProfileComponent from './components/ProfileComponent.vue'
import AuthSection from './components/AuthSection.vue'
import LeaderSection from './components/LeaderSection.vue'
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Roboto", sans-serif;
}

.main-content {
  padding: 30px 50px;
}

.plus-icon {
  margin-top: -15px;
  text-align: center;
}

.plus-btn {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: 2px solid rgba(19, 39, 96, 1);
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  color: rgba(19, 39, 96, 1);
  cursor: pointer;
}

.mobile-only {
  display: none !important; 
}

.desktop-only {
  display: block;
}

@media (max-width: 768px) {
  body {
    background: #f9fafd;
  }
  
  .desktop-only {
    display: none;
  }

  .mobile-only {
    display: block;
  }

  .main-content {
    padding: 0;
  }
}
</style>