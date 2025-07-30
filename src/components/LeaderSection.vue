<template>
  <div class="form-sections">
    <h3 class="form-sections-title mobile-only">Leader</h3>

    <div class="form-section auth-section">
      <h3 class="desktop-only">Leader</h3>
      <div class="form-group">
        <label>I want to be a leader</label>
        <div class="form-link">It's a leadership application form</div>
      </div>
      
      <div class="form-wrapper">
        <div class="form-group">
          <label>Select Project</label>
        </div>

        <div class="form-group">
          <select 
            v-if="isMobile" 
            v-model="selectedProject" 
            class="input-underline mobile-only"
          >
            <option value="">Name of the project</option>
            <option value="project1">Project 1</option>
            <option value="project2">Project 2</option>
          </select>
          <input 
            v-else
            v-model="selectedProject"
            type="text" 
            placeholder="Name of the project" 
            class="input-underline desktop-only" 
          />
        </div>

        <div class="form-group">
          <label>Comment</label>
          <textarea 
            v-model="comment"
            class="textarea-underline" 
            rows="4" 
            placeholder=""
          ></textarea>
        </div>
        
        <div class="form-group">
          <button class="btn-like" @click="sendRequest">Send Request</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const selectedProject = ref('')
const comment = ref('')
const windowWidth = ref(window.innerWidth)

const isMobile = computed(() => windowWidth.value <= 768)

const updateWindowWidth = () => {
  windowWidth.value = window.innerWidth
}

const sendRequest = () => {
  console.log('Sending leadership request:', {
    project: selectedProject.value,
    comment: comment.value
  })
}

onMounted(() => {
  window.addEventListener('resize', updateWindowWidth)
})

onUnmounted(() => {
  window.removeEventListener('resize', updateWindowWidth)
})
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

.form-group .form-link {
  font-size: 14px;
  color: #999;
  text-decoration: none;
  cursor: pointer;
}

.form-wrapper {
  display: flex;
  flex-direction: column;
  gap: 15px;
  background: rgba(243, 245, 251, 1);
  padding: 20px;
}

.form-wrapper .form-group label {
  color: #132760;
}

.input-underline,
.textarea-underline {
  width: 100%;
  border: none;
  border-bottom: 1px solid #132760;
  background: transparent;
  padding: 5px 0;
  font-size: 14px;
  outline: none;
  resize: none;
  color: #132760;
}

.input-underline::placeholder {
  color: #132760;
}

.btn-like {
  text-align: center;
  padding: 12px;
  border: 1px solid rgba(19, 39, 96, 1);
  background: transparent;
  width: 100%;
  cursor: pointer;
  color: rgba(19, 39, 96, 1);
}

.btn-like:hover {
  background: rgba(19, 39, 96, 0.1);
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

  .form-section {
    padding: 15px;
    box-shadow: none;
  }

  .form-section h3 {
    font-size: 16px;
    margin-bottom: 15px;
  }

  .form-wrapper {
    padding: 15px;
    background: transparent;
  }

  .form-sections-title {
    display: block;
  }
  
  .btn-like {
    text-align: center;
    padding: 12px;
    border: 1px solid rgba(19, 39, 96, 1);
    background: transparent;
    width: 100%;
  }
}
</style>