<template>
  <div class="mobile-header">
    Account settings 
    <img :src="Vector1" alt="">
  </div>
  <div class="mobile-section-title">Personal information</div>
</template>
<script setup>
import Vector1 from '@/assets/Vector1.png'
</script>
<style scoped>
.mobile-header {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 20px;
  font-weight: 500;
  color: rgba(19, 39, 96, 1);
  padding: 20px;
}

.mobile-section-title {
  font-size: 16px;
  color: rgba(19, 39, 96, 1);
  padding: 20px;
  padding-top: 5px;
}
@media screen and (min-width: 769px) {
  .mobile-header, .mobile-section-title {
    display: none;
  }
    
}
</style>