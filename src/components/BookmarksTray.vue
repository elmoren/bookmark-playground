<template>
  <div v-if="isTrayOpen" class="bookmarks-tray">
    <div v-for="bookmark in bookmarks" :key="bookmark.name" class="bookmark-item">
      <a :href="bookmark.link" target="_blank">{{ bookmark.name }}</a>
    </div>
  </div>
</template>

<script setup>
defineProps({
  bookmarks: {
    type: Array,
    required: true
  },
  isTrayOpen: {
    type: Boolean,
    required: true
  }
});
</script>

<style scoped>
.bookmarks-tray {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 5px; /* Reduced space between grid items */
  position: absolute;
  background-color: #f1f1f1;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 999; /* Ensure it's above other content */
  top: 100%;
  left: 0;
  width: 100%;
  padding: 5px; /* Reduced padding */
}

.bookmark-item a {
  color: black;
  padding: 5px 8px; /* Further reduced padding for grid items */
  text-decoration: none;
  display: block;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  border: 1px solid #eee;
  background-color: #fff;
}

.bookmark-item a:hover {
  background-color: #ddd;
}
</style>
