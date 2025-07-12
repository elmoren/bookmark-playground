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
  display: block;
  position: absolute;
  background-color: #f1f1f1;
  max-height: 400px;
  overflow-y: auto;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 999; /* Ensure it's above other content */
  top: 100%;
  left: 0;
  width: 100%;
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
