<template>
  <div :class="{ 'dark-mode': isDarkMode }">
    <header>
      
    </header>
  
    <router-view/>
    
    <button @click="toggleDarkMode" class="btn btn-toggle">
      {{ isDarkMode ? 'Switch to Light Mode' : 'Switch to Dark Mode' }}
    </button>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const isDarkMode = ref(false);

onMounted(() => {
  const savedMode = localStorage.getItem('darkMode');
  if (savedMode) {
    isDarkMode.value = JSON.parse(savedMode);
    document.body.classList.toggle('dark-mode', isDarkMode.value);
  }
});

const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value;
  localStorage.setItem('darkMode', JSON.stringify(isDarkMode.value));
  document.body.classList.toggle('dark-mode', isDarkMode.value);
};
</script>

<style>
.dark-mode {
  background-color: #121212; 
  color: #e0e0e0; 
}

.dark-mode header {
  background-color: #1f1f1f; 
}

.dark-mode button.btn-toggle {
  background-color: #333;
  color: #e0e0e0;
  border: none;
}

.dark-mode button.btn-toggle:hover {
  background-color: #444;
}


.btn-toggle {
  margin-top: -10px;
  position:relative;
  bottom: 10%; 
  left: 50%; 
  transform: translateX(-50%); 
 
}
</style>
