<template>
  <div class="form-sections">
    <h3 class="form-sections-title mobile-only">Auth data</h3>

    <div class="form-section auth-section">
      <h3 class="desktop-only">Auth data</h3>
      <div class="form-group">
        <label>Password</label>
        <div class="form-link" @click="changePassword">change password</div>
      </div>
      <div class="form-group">
        <label>Email</label>
        <div class="form-value">mykola.lisovskyi@realtybundles.com</div>
        <div class="form-link" @click="changeEmail">change email</div>
      </div>
    </div>
    
    <h3 class="form-sections-title mobile-only">Messages</h3>

    <div class="form-section messages-section">
      <h3 class="desktop-only">Messages</h3>
      <div class="messages-content">
      </div>
    </div>
  </div>
</template>

<script setup>
const changePassword = () => {
  console.log('Change password clicked')
}

const changeEmail = () => {
  console.log('Change email clicked')
}
</script>

<style scoped>
.form-sections {
  display: flex;
  flex-direction: row;
  gap: 20px;
  margin-top: 30px;
}

.form-section {
  background: white;
  border: 1px solid #e0e0e0;
  padding: 20px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.form-section.auth-section {
  flex: 0 0 30%;
}

.form-section.messages-section {
  flex: 1;
}

.form-section h3 {
  font-size: 18px;
  color: rgba(19, 39, 96, 1);
  margin-bottom: 20px;
  font-weight: 800;
}

.form-group {
  margin-bottom: 15px;
}

.form-group:last-child {
  margin-bottom: 0;
}

.form-group label {
  font-size: 16px;
  color: rgba(19, 39, 96, 1);
  margin-bottom: 5px;
  display: block;
  font-weight: 500;
}

.form-group .form-value {
  font-size: 16px;
  color: #333;
  margin-bottom: 5px;
}

.form-group .form-link {
  font-size: 14px;
  color: #999;
  text-decoration: none;
  cursor: pointer;
}

.form-group .form-link:hover {
  color: #007bff;
  text-decoration: underline;
}

.messages-content {
  height: 150px;
  background: transparent;
}

.form-sections-title {
  font-size: 18px;
  color: rgba(19, 39, 96, 1);
  padding-left: 20px;
  display: none;
}

@media (max-width: 768px) {
  .form-sections {
    flex-direction: column;
    gap: 15px;
  }

  .form-section.auth-section {
    flex: none;
    width: 320px;
    display: block;
    margin: 0 auto;
    border: 1px solid rgba(219, 220, 221, 1);
    box-shadow: none;
  }

  .form-section.messages-section {
    flex: none;
    width: 320px;
    display: block;
    margin: 0 auto;
    border: 1px solid rgba(219, 220, 221, 1);
    box-shadow: none;
  }

  .form-section {
    padding: 15px;
    box-shadow: none;
  }

  .form-section h3 {
    font-size: 16px;
    margin-bottom: 15px;
  }

  .form-group label {
    font-size: 14px;
  }

  .form-group .form-value {
    font-size: 14px;
  }

  .form-group .form-link {
    font-size: 13px;
  }

  .messages-content {
    height: 100px;
  }

  .form-sections-title {
    display: block;
  }
}
</style>