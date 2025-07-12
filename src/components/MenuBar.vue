<template>
  <div class="menu-bar">
    <div class="menu-bar-left">
      <div class="dropdown">
        <button class="dropdown-button">Menu</button>
        <div class="dropdown-content">
          <a href="#">Item 1</a>
          <a href="#">Item 2</a>
          <a href="#">Item 3</a>
        </div>
      </div>
    </div>
    <div class="menu-bar-right">
      <span>Username</span>
      <button @click="toggleBookmarksTray" class="bookmarks-button">Bookmarks</button>
    </div>
    <BookmarksTray :bookmarks="bookmarks" :isTrayOpen="isBookmarksTrayOpen" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import BookmarksTray from './BookmarksTray.vue';

const props = defineProps({
  bookmarks: {
    type: Array,
    required: true
  }
});

const isBookmarksTrayOpen = ref(false);

function toggleBookmarksTray() {
  isBookmarksTrayOpen.value = !isBookmarksTrayOpen.value;
}
</script>

<style scoped>
.menu-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px 20px;
  background-color: #f8f9fa;
  border-bottom: 1px solid #dee2e6;
  position: sticky;
  top: 0;
  left: 0;
  width: 100%;
  box-sizing: border-box;
  z-index: 1000;
}

.menu-bar-left, .menu-bar-right {
  display: flex;
  align-items: center;
}

.dropdown {
  position: relative;
  display: inline-block;
}

.dropdown-button {
  background-color: #007bff;
  color: white;
  padding: 10px;
  font-size: 16px;
  border: none;
  cursor: pointer;
}

.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f1f1f1;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 1;
}

.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}

.dropdown-content a:hover {
  background-color: #ddd;
}

.dropdown:hover .dropdown-content {
  display: block;
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
</style>
