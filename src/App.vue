<script setup>
import { ref } from 'vue';
import MenuBar from './components/MenuBar.vue';

const bookmarks = ref([]);

function generateBookmarks(count) {
  const newBookmarks = [];
  let i = 1;
  while (i <= count) {
    // After 3 individual bookmarks, create a folder.
    if (i % 8 === 4 && (count - i) >= 4) {
      const folder = {
        name: `Folder ${Math.ceil(i / 8)}`,
        children: []
      };
      for (let j = 0; j < 4; j++) {
        folder.children.push({ name: `Bookmark ${i++}`, link: `` });
      }
      newBookmarks.push(folder);
    } else {
      newBookmarks.push({ name: `Bookmark ${i++}`, link: `` });
    }
  }
  bookmarks.value = newBookmarks;
}

// Initialize with 20 bookmarks
generateBookmarks(20);
</script>

<template>
  <MenuBar :bookmarks="bookmarks" />
  <main>
    <div class="bookmark-controls">
      <button @click="generateBookmarks(0)">0 Bookmarks</button>
      <button @click="generateBookmarks(20)">20 Bookmarks</button>
      <button @click="generateBookmarks(50)">50 Bookmarks</button>
      <button @click="generateBookmarks(100)">100 Bookmarks</button>
      <button @click="generateBookmarks(200)">200 Bookmarks</button>
    </div>
  </main>
</template>

<style>
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "Noto Sans", sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
}

.bookmark-controls {
  padding: 20px;
  display: flex;
  gap: 10px;
  justify-content: center;
}

.bookmark-controls button {
  background-color: #007bff;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

.bookmark-controls button:hover {
  background-color: #0056b3;
}
</style>
