<template>
  <div class="profile-container">
    <div class="profile-left desktop-only">
      <div class="profile-avatar">
        Test R
      </div>
      <div class="camera-placeholder">
        <img src="/assets/Vector.png" alt="Camera" @click="uploadPhoto">
      </div>
    </div>

    <div class="mobile-only mob-bg">
      <div class="profile-avatar">
        Test R
      </div>
      <div class="mobile-avatar">
        <img src="/assets/Vector.png" alt="Camera" @click="uploadPhoto">
      </div>
    </div>

    <div class="profile-info">
      <div class="info-group">
        <div class="info-label">Country</div>
        <input class="info-value" v-model="userData.country">
      </div>

      <div class="info-group">
        <div class="info-label">ID Code</div>
        <input class="info-value" v-model="userData.idCode">
      </div>

      <div class="info-group">
        <div class="info-label">Facebook</div>
        <input class="info-value" placeholder="need to add" v-model="userData.facebook">
      </div>

      <div class="info-group">
        <div class="info-label">Phones</div>
        <input class="info-value" placeholder="need to add" v-model="userData.phones">
      </div>

      <div class="info-group">
        <div class="info-label">Address</div>
        <input class="info-value" v-model="userData.address">
      </div>

      <div class="info-group">
        <div class="info-label">Birthday</div>
        <input class="info-value" type="date" v-model="userData.birthday">
      </div>

      <div class="info-group">
        <div class="info-label">LinkedIn</div>
        <input class="info-value" placeholder="need to add" v-model="userData.linkedin">
      </div>

      <div class="info-group">
        <div class="info-label" style="color: #ff6b35;">Mobile</div>
        <input class="info-value" v-model="userData.mobile">
      </div>

      <div class="info-group">
        <div class="info-label" style="color: #ff6b35;">Postcode</div>
        <input class="info-value" v-model="userData.postcode">
      </div>

      <div class="info-group">
        <div class="info-label">ID Photo</div>
        <input class="info-value" value="✓" readonly>
      </div>

      <div class="info-group">
        <div class="info-label">Home</div>
        <input class="info-value" v-model="userData.home">
      </div>

      <div class="info-group mobile-only">
        <div class="info-label">Phone</div>
        <div class="mobile-phone-input">
          <div class="country-flag">+972↓</div>
          <input class="info-value" v-model="userData.phone">
        </div>
      </div>

      <div class="interests-section">
        <div class="interests-container">
          <div class="info-label">Interests</div>
          
          <div class="interests-list">
            <div 
              v-for="interest in interests" 
              :key="interest.id" 
              class="interest-item"
            >
              <input 
                type="checkbox" 
                :id="interest.id" 
                class="interest-checkbox"
                :checked="userData.interests.includes(interest.id)"
                @change="toggleInterest(interest.id)"
              >
              <label :for="interest.id" class="interest-label">
                {{ interest.label }}
              </label>
            </div>
          </div>
          
          <button class="save-btn" @click="saveProfile">Save</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const userData = ref({
  country: 'Israel',
  idCode: '134275638',
  facebook: 'david_22',
  phones: '',
  address: 'Tel Aviv-Yafo, Shabazi 55',
  birthday: '',
  linkedin: 'david_22',
  mobile: '',
  postcode: '',
  home: 'need to add',
  phone: '5440553422',
  interests: []
})

const interests = ref([
  { id: 'high-tech', label: 'High-tech' },
  { id: 'medicine', label: 'Medicine' },
  { id: 'money', label: 'Money' },
  { id: 'sentences', label: 'Sentences' },
  { id: 'independent', label: 'Independent' },
  { id: 'other', label: 'Other' }
])

const toggleInterest = (interestId) => {
  const currentInterests = [...userData.value.interests]
  const index = currentInterests.indexOf(interestId)
  
  if (index > -1) {
    currentInterests.splice(index, 1)
  } else {
    currentInterests.push(interestId)
  }
  
  userData.value.interests = currentInterests
}

const saveProfile = () => {
  console.log('Saving profile:', userData.value)
}

const uploadPhoto = () => {
  console.log('Upload photo clicked')
}
</script>

<style scoped>
.profile-container {
  background: white;
  display: flex;
  gap: 40px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.profile-left {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 20px;
  flex-shrink: 0;
}

.profile-avatar {
  width: 220px;
  height: 260px;
  background-color: rgba(19, 39, 96, 1);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 24px;
  font-weight: 500;
}

.camera-placeholder {
  width: 109px;
  height: 109px;
  background-color: #e0e0e0;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #666;
  font-size: 24px;
  cursor: pointer;
}

.profile-info {
  flex: 1;
  display: grid;
  grid-template-columns: 1.4fr 1fr 1fr 1fr;
  gap: 15px 20px;
  align-content: start;
  padding-top: 15px;
}

.info-group {
  display: flex;
  flex-direction: row;
    align-items: center;
  gap: 15px;
}

.info-label {
  font-size: 16px;
  color: rgba(19, 39, 96, 1);
  font-weight: 700;
  white-space: nowrap; 
}

.info-value {
  font-size: 16px;
  color: #333;
  border: none;
  background: transparent;
  outline: none;
  padding: 0;
  margin: 0;
  width: 100%; 
  transition: border-color 0.2s, box-shadow 0.2s;
}

.info-value::placeholder {
  color: rgba(113, 113, 113, 1);
}

.info-value:hover {
  border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  cursor: text;
}

.info-value:focus {
  border-bottom: 1px solid rgba(0, 0, 0, 0.25);
}

.interests-section {
  grid-column: 1 / -1;
  margin-top: 20px;
}

.interests-container {
  display: flex;
  align-items: center;
  justify-content: space-around;
  margin-top: 15px;
}

.interests-list {
  display: flex;
  gap: 20px;
  align-items: center;
}

.interests-list .info-label {
  margin-left: -70px;
}

.interest-item {
  display: flex;
  align-items: center;
  gap: 8px;
}

.interest-checkbox {
  appearance: none;
  -webkit-appearance: none;
  width: 18px;
  height: 18px;
  border: 2px solid #ccc;
  border-radius: 1px;
  position: relative;
  cursor: pointer;
}

.interest-checkbox:checked {
  background-color: rgba(144, 181, 63, 1);
  border-color: rgba(144, 181, 63, 1);
}

.interest-checkbox:checked::after {
  content: "✓";
  color: white;
  position: absolute;
  top: -2px;
  left: 2px;
  font-size: 14px;
}

.interest-label {
  font-size: 16px;
  color: #333;
  cursor: pointer;
}

.save-btn {
  background-color: rgba(144, 181, 63, 1);
  color: white;
  border: none;
  padding: 12px 30px;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  flex-shrink: 0;
}

.mobile-phone-input {
  display: flex;
  gap: 10px;
  align-items: center;
}
@media screen and (min-width: 768px) {
  .mobile-phone-input
  {
    display: none;
  }
}
.country-flag {
  display: flex;
  align-items: center;
  gap: 5px;
  padding: 8px;
  border: 1px solid #ddd;
  border-radius: 4px;
  font-size: 14px;
}

.mobile-avatar {
  width: 100px;
  height: 100px;
  background-color: #e0e0e0;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 20px auto;
  color: #666;
  font-size: 24px;
  cursor: pointer;
}

.mob-bg {
  background: #ffffff;
  border: 1px solid rgba(219, 220, 221, 1);
}

@media (max-width: 768px) {
  .profile-container {
    border-radius: 0;
    box-shadow: none;
    padding: 20px;
    flex-direction: column;
    gap: 20px;
    background: #f9fafd;
  }

  .profile-left {
    display: none;
  }

  .profile-avatar {
    width: 100%;
    height: 60px;
    margin-bottom: 20px;
  }

  .profile-info {
    grid-template-columns: 1fr;
    gap: 15px;
    padding: 15px;
    border: 1px solid #ddd;
    background: white;
  }
  
  .info-group {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .info-value {
    font-size: 14px;
    border: 1px solid #ddd;
    display: block;
    width: 100%;
    padding: 10px;
  }
  
  .info-value:hover {
    border: 1px solid #ddd;
  }

  .info-value:focus {
    border: 1px solid #ddd;
  }
  
  .interests-container {
    flex-direction: column;
    align-items: stretch;
  }

  .interests-list {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 12px 20px;
  }

  .interests-list .info-label {
    margin-left: 0;
    margin-top: -60px;
  }

  .save-btn {
    width: 100%;
    margin: 20px 0 0 0;
  }
}
@media screen and (min-width: 768px) {

  .mobile-only {
    display: none;
  }
  
}
</style>