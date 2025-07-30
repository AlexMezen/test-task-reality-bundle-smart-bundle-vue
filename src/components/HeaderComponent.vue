<template>
  <div class="header">
    <div class="header-left">
      <span>
        <img :src="accountCircleIcon" alt=""> 
        Test
      </span>
      <span>Profile</span>
      <span @click="logout">Logout</span>
    </div>
    <div class="header-right">
      <div class="lang-switcher">
        <span 
          @click="switchLanguage('HE')" 
          :class="{ 'lang-active': currentLanguage === 'HE' }"
        >
          HE
        </span>
        <span 
          @click="switchLanguage('EN')" 
          :class="{ 'lang-active': currentLanguage === 'EN' }"
        >
          EN
        </span>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import accountCircleIcon from '@/assets/account_circle_FILL1_wght300_GRAD0_opsz24 1.png'
const currentLanguage = ref('EN')

const switchLanguage = (lang) => {
  currentLanguage.value = lang
}

const logout = () => {
  console.log('Logout clicked')
}
</script>

<style scoped>
.header {
  background-color: rgba(19, 39, 96, 1);
  color: white;
  padding: 10px 150px 10px 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 16px;
}

.header-left {
  display: flex;
  gap: 20px;
}

.header-left span {
  display: flex;
  align-items: center;
  gap: 5px;
  cursor: pointer;
}

.header-right {
  display: flex;
  align-items: center;
  gap: 15px;
}

.lang-switcher {
  display: flex;
  gap: 5px;
}

.lang-switcher span {
  cursor: pointer;
  padding: 2px 4px;
}

.lang-active {
  color: rgba(144, 181, 63, 1);
}
@media (max-width: 768px) {
  .header {
    display: none;
  }
}
</style>