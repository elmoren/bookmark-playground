<template>
  <div v-if="isTrayOpen" class="bookmarks-tray">
    <div class="bookmarks-grid" ref="bookmarksGridRef">
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
import { ref, computed, watch, onMounted, onUnmounted } from 'vue';

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

const bookmarksGridRef = ref(null);
const currentPage = ref(1);
const itemsPerPage = ref(100);

// Function to calculate items per page based on current window size
function calculateItemsPerPage() {
  if (!bookmarksGridRef.value) return;

  const gridHeight = bookmarksGridRef.value.offsetHeight;
  const gridWidth = bookmarksGridRef.value.offsetWidth;

  const estimatedRows = 15; // Fixed number of rows
  const estimatedColumns = Math.min(6, Math.floor(gridWidth / 254));

  // Ensure at least 1 column
  const actualColumns = Math.max(1, estimatedColumns);

  itemsPerPage.value = estimatedRows * actualColumns;
  if (itemsPerPage.value === 0) itemsPerPage.value = 1;
}

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
  calculateItemsPerPage();
});

watch(() => props.isTrayOpen, (newValue) => {
  if (newValue) {
    currentPage.value = 1;
    calculateItemsPerPage();
  }
});

onMounted(() => {
  calculateItemsPerPage();
  window.addEventListener('resize', calculateItemsPerPage);
});

onUnmounted(() => {
  window.removeEventListener('resize', calculateItemsPerPage);
});

</script>

<style scoped>
.bookmarks-tray {
  display: flex;
  flex-direction: column;
  position: absolute;
  background-color: #f5f5f5;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  z-index: 999; /* Ensure it's above other content */
  top: 105%;
  left: 0;
  width: 100%;
  padding: 5px;
  min-height: 600px; /* Keep min-height for small content */
  max-height: 90dvh; /* Set max-height to a percentage of viewport height */
  overflow-y: auto; /* Enable vertical scrolling */
}

.bookmarks-grid {
  display: grid;
  grid-auto-flow: column; /* Fill columns first */
  grid-template-rows: repeat(15, minmax(min-content, max-content)); /* Fixed 15 rows */
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); /* Ensure columns are wide enough */
  gap: 4px;
  flex-grow: 1; /* Allow grid to take available height */
  /* Removed height: 100%; */
}

.bookmark-item a {
  color: black;
  padding: 3px 5px;
  text-decoration: none;
  display: block;
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
