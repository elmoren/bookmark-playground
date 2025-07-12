<template>
  <div v-if="isTrayOpen" class="bookmarks-tray">
    <div class="bookmarks-grid">
      <div v-for="bookmark in paginatedBookmarks" :key="bookmark.name" class="bookmark-item">
        <a :href="bookmark.link" target="_blank">{{ bookmark.name }}</a>
      </div>
    </div>
    <div class="pagination-controls">
      <span @click="prevPage" :class="{ disabled: currentPage === 1 }" class="arrow">&laquo;</span>
      <span v-for="page in totalPages" :key="page" @click="currentPage = page" :class="{ active: currentPage === page }" class="dot"></span>
      <span @click="nextPage" :class="{ disabled: currentPage === totalPages }" class="arrow">&raquo;</span>
    </div>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';

const props = defineProps({
  bookmarks: {
    type: Array,
    required: true
  },
  isTrayOpen: {
    type: Boolean,
    required: true
  }
});

const currentPage = ref(1);
const itemsPerPage = ref(50); // Adjust this value based on desired items per page

const paginatedBookmarks = computed(() => {
  const start = (currentPage.value - 1) * itemsPerPage.value;
  const end = start + itemsPerPage.value;
  return props.bookmarks.slice(start, end);
});

const totalPages = computed(() => {
  return Math.ceil(props.bookmarks.length / itemsPerPage.value);
});

function nextPage() {
  if (currentPage.value < totalPages.value) {
    currentPage.value++;
  }
}

function prevPage() {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
}

// Reset to first page when bookmarks change or tray opens/closes
watch(() => props.bookmarks, () => {
  currentPage.value = 1;
});

watch(() => props.isTrayOpen, (newValue) => {
  if (newValue) {
    currentPage.value = 1;
  }
});
</script>

<style scoped>
.bookmarks-tray {
  display: flex;
  flex-direction: column;
  position: absolute;
  background-color: #f1f1f1;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 999; /* Ensure it's above other content */
  top: 100%;
  left: 0;
  width: 100%;
  padding: 5px;
}

.bookmarks-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); /* Increased min-width for full text visibility */
  gap: 3px;
  padding-bottom: 10px; /* Space for pagination controls */
}

.bookmark-item a {
  color: black;
  padding: 3px 5px;
  text-decoration: none;
  display: block;
  /* Removed text truncation properties */
  border: 1px solid #eee;
  background-color: #fff;
}

.bookmark-item a:hover {
  background-color: #ddd;
}

.pagination-controls {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 10px 0;
  border-top: 1px solid #eee;
}

.arrow {
  cursor: pointer;
  padding: 0 10px;
  font-size: 20px;
  user-select: none; /* Prevent text selection */
}

.arrow.disabled {
  color: #ccc;
  cursor: not-allowed;
}

.dot {
  cursor: pointer;
  height: 10px;
  width: 10px;
  margin: 0 5px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

.dot.active {
  background-color: #717171;
}
</style>
