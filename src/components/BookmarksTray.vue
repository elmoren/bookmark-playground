<template>
  <div class="bookmarks-tray-container">
    <button @click="toggleTray" class="bookmarks-button">Bookmarks</button>
    <div v-if="isTrayOpen" class="bookmarks-tray">
      <div v-for="bookmark in bookmarks" :key="bookmark.name" class="bookmark-item">
        <a :href="bookmark.link" target="_blank">{{ bookmark.name }}</a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

defineProps({
  bookmarks: {
    type: Array,
    required: true
  }
});

const isTrayOpen = ref(false);

function toggleTray() {
  isTrayOpen.value = !isTrayOpen.value;
}
</script>

<style scoped>
.bookmarks-tray-container {
  position: relative;
  display: inline-block;
}

.bookmarks-button {
  background-color: #007bff;
  color: white;
  padding: 10px;
  font-size: 16px;
  border: none;
  cursor: pointer;
  margin-left: 10px;
}

.bookmarks-tray {
  display: block;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 200px;
  max-height: 400px;
  overflow-y: auto;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
  right: 0;
}

.bookmark-item a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.bookmark-item a:hover {
  background-color: #ddd;
}
</style>
