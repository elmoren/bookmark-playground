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

const isBookmarksTrayOpen = ref(false);

const bookmarks = ref([
  { name: 'Google', link: 'https://google.com' },
  { name: 'Facebook', link: 'https://facebook.com' },
  { name: 'Apple', link: 'https://apple.com' },
  { name: 'Amazon', link: 'https://amazon.com' },
  { name: 'Microsoft', link: 'https://microsoft.com' },
  { name: 'Bookmark 6', link: 'https://example.com/6' },
  { name: 'Bookmark 7', link: 'https://example.com/7' },
  { name: 'Bookmark 8', link: 'https://example.com/8' },
  { name: 'Bookmark 9', link: 'https://example.com/9' },
  { name: 'Bookmark 10', link: 'https://example.com/10' },
  { name: 'Bookmark 11', link: 'https://example.com/11' },
  { name: 'Bookmark 12', link: 'https://example.com/12' },
  { name: 'Bookmark 13', link: 'https://example.com/13' },
  { name: 'Bookmark 14', link: 'https://example.com/14' },
  { name: 'Bookmark 15', link: 'https://example.com/15' },
  { name: 'Bookmark 16', link: 'https://example.com/16' },
  { name: 'Bookmark 17', link: 'https://example.com/17' },
  { name: 'Bookmark 18', link: 'https://example.com/18' },
  { name: 'Bookmark 19', link: 'https://example.com/19' },
  { name: 'Bookmark 20', link: 'https://example.com/20' },
  { name: 'Bookmark 21', link: 'https://example.com/21' },
  { name: 'Bookmark 22', link: 'https://example.com/22' },
  { name: 'Bookmark 23', link: 'https://example.com/23' },
  { name: 'Bookmark 24', link: 'https://example.com/24' },
  { name: 'Bookmark 25', link: 'https://example.com/25' },
  { name: 'Bookmark 26', link: 'https://example.com/26' },
  { name: 'Bookmark 27', link: 'https://example.com/27' },
  { name: 'Bookmark 28', link: 'https://example.com/28' },
  { name: 'Bookmark 29', link: 'https://example.com/29' },
  { name: 'Bookmark 30', link: 'https://example.com/30' },
  { name: 'Bookmark 31', link: 'https://example.com/31' },
  { name: 'Bookmark 32', link: 'https://example.com/32' },
  { name: 'Bookmark 33', link: 'https://example.com/33' },
  { name: 'Bookmark 34', link: 'https://example.com/34' },
  { name: 'Bookmark 35', link: 'https://example.com/35' },
  { name: 'Bookmark 36', link: 'https://example.com/36' },
  { name: 'Bookmark 37', link: 'https://example.com/37' },
  { name: 'Bookmark 38', link: 'https://example.com/38' },
  { name: 'Bookmark 39', link: 'https://example.com/39' },
  { name: 'Bookmark 40', link: 'https://example.com/40' },
  { name: 'Bookmark 41', link: 'https://example.com/41' },
  { name: 'Bookmark 42', link: 'https://example.com/42' },
  { name: 'Bookmark 43', link: 'https://example.com/43' },
  { name: 'Bookmark 44', link: 'https://example.com/44' },
  { name: 'Bookmark 45', link: 'https://example.com/45' },
  { name: 'Bookmark 46', link: 'https://example.com/46' },
  { name: 'Bookmark 47', link: 'https://example.com/47' },
  { name: 'Bookmark 48', link: 'https://example.com/48' },
  { name: 'Bookmark 49', link: 'https://example.com/49' },
  { name: 'Bookmark 50', link: 'https://example.com/50' },
  { name: 'Bookmark 51', link: 'https://example.com/51' },
  { name: 'Bookmark 52', link: 'https://example.com/52' },
  { name: 'Bookmark 53', link: 'https://example.com/53' },
  { name: 'Bookmark 54', link: 'https://example.com/54' },
  { name: 'Bookmark 55', link: 'https://example.com/55' },
  { name: 'Bookmark 56', link: 'https://example.com/56' },
  { name: 'Bookmark 57', link: 'https://example.com/57' },
  { name: 'Bookmark 58', link: 'https://example.com/58' },
  { name: 'Bookmark 59', link: 'https://example.com/59' },
  { name: 'Bookmark 60', link: 'https://example.com/60' },
  { name: 'Bookmark 61', link: 'https://example.com/61' },
  { name: 'Bookmark 62', link: 'https://example.com/62' },
  { name: 'Bookmark 63', link: 'https://example.com/63' },
  { name: 'Bookmark 64', link: 'https://example.com/64' },
  { name: 'Bookmark 65', link: 'https://example.com/65' },
  { name: 'Bookmark 66', link: 'https://example.com/66' },
  { name: 'Bookmark 67', link: 'https://example.com/67' },
  { name: 'Bookmark 68', link: 'https://example.com/68' },
  { name: 'Bookmark 69', link: 'https://example.com/69' },
  { name: 'Bookmark 70', link: 'https://example.com/70' },
  { name: 'Bookmark 71', link: 'https://example.com/71' },
  { name: 'Bookmark 72', link: 'https://example.com/72' },
  { name: 'Bookmark 73', link: 'https://example.com/73' },
  { name: 'Bookmark 74', link: 'https://example.com/74' },
  { name: 'Bookmark 75', link: 'https://example.com/75' },
  { name: 'Bookmark 76', link: 'https://example.com/76' },
  { name: 'Bookmark 77', link: 'https://example.com/77' },
  { name: 'Bookmark 78', link: 'https://example.com/78' },
  { name: 'Bookmark 79', link: 'https://example.com/79' },
  { name: 'Bookmark 80', link: 'https://example.com/80' },
  { name: 'Bookmark 81', link: 'https://example.com/81' },
  { name: 'Bookmark 82', link: 'https://example.com/82' },
  { name: 'Bookmark 83', link: 'https://example.com/83' },
  { name: 'Bookmark 84', link: 'https://example.com/84' },
  { name: 'Bookmark 85', link: 'https://example.com/85' },
  { name: 'Bookmark 86', link: 'https://example.com/86' },
  { name: 'Bookmark 87', link: 'https://example.com/87' },
  { name: 'Bookmark 88', link: 'https://example.com/88' },
  { name: 'Bookmark 89', link: 'https://example.com/89' },
  { name: 'Bookmark 90', link: 'https://example.com/90' },
  { name: 'Bookmark 91', link: 'https://example.com/91' },
  { name: 'Bookmark 92', link: 'https://example.com/92' },
  { name: 'Bookmark 93', link: 'https://example.com/93' },
  { name: 'Bookmark 94', link: 'https://example.com/94' },
  { name: 'Bookmark 95', link: 'https://example.com/95' },
  { name: 'Bookmark 96', link: 'https://example.com/96' },
  { name: 'Bookmark 97', link: 'https://example.com/97' },
  { name: 'Bookmark 98', link: 'https://example.com/98' },
  { name: 'Bookmark 99', link: 'https://example.com/99' },
  { name: 'Bookmark 100', link: 'https://example.com/100' },
  { name: 'Bookmark 101', link: 'https://example.com/101' },
  { name: 'Bookmark 102', link: 'https://example.com/102' },
  { name: 'Bookmark 103', link: 'https://example.com/103' },
  { name: 'Bookmark 104', link: 'https://example.com/104' },
  { name: 'Bookmark 105', link: 'https://example.com/105' },
  { name: 'Bookmark 106', link: 'https://example.com/106' },
  { name: 'Bookmark 107', link: 'https://example.com/107' },
  { name: 'Bookmark 108', link: 'https://example.com/108' },
  { name: 'Bookmark 109', link: 'https://example.com/109' },
  { name: 'Bookmark 110', link: 'https://example.com/110' },
  { name: 'Bookmark 111', link: 'https://example.com/111' },
  { name: 'Bookmark 112', link: 'https://example.com/112' },
  { name: 'Bookmark 113', link: 'https://example.com/113' },
  { name: 'Bookmark 114', link: 'https://example.com/114' },
  { name: 'Bookmark 115', link: 'https://example.com/115' },
  { name: 'Bookmark 116', link: 'https://example.com/116' },
  { name: 'Bookmark 117', link: 'https://example.com/117' },
  { name: 'Bookmark 118', link: 'https://example.com/118' },
  { name: 'Bookmark 119', link: 'https://example.com/119' },
  { name: 'Bookmark 120', link: 'https://example.com/120' },
  { name: 'Bookmark 121', link: 'https://example.com/121' },
  { name: 'Bookmark 122', link: 'https://example.com/122' },
  { name: 'Bookmark 123', link: 'https://example.com/123' },
  { name: 'Bookmark 124', link: 'https://example.com/124' },
  { name: 'Bookmark 125', link: 'https://example.com/125' },
  { name: 'Bookmark 126', link: 'https://example.com/126' },
  { name: 'Bookmark 127', link: 'https://example.com/127' },
  { name: 'Bookmark 128', link: 'https://example.com/128' },
  { name: 'Bookmark 129', link: 'https://example.com/129' },
  { name: 'Bookmark 130', link: 'https://example.com/130' },
  { name: 'Bookmark 131', link: 'https://example.com/131' },
  { name: 'Bookmark 132', link: 'https://example.com/132' },
  { name: 'Bookmark 133', link: 'https://example.com/133' },
  { name: 'Bookmark 134', link: 'https://example.com/134' },
  { name: 'Bookmark 135', link: 'https://example.com/135' },
  { name: 'Bookmark 136', link: 'https://example.com/136' },
  { name: 'Bookmark 137', link: 'https://example.com/137' },
  { name: 'Bookmark 138', link: 'https://example.com/138' },
  { name: 'Bookmark 139', link: 'https://example.com/139' },
  { name: 'Bookmark 140', link: 'https://example.com/140' },
  { name: 'Bookmark 141', link: 'https://example.com/141' },
  { name: 'Bookmark 142', link: 'https://example.com/142' },
  { name: 'Bookmark 143', link: 'https://example.com/143' },
  { name: 'Bookmark 144', link: 'https://example.com/144' },
  { name: 'Bookmark 145', link: 'https://example.com/145' },
  { name: 'Bookmark 146', link: 'https://example.com/146' },
  { name: 'Bookmark 147', link: 'https://example.com/147' },
  { name: 'Bookmark 148', link: 'https://example.com/148' },
  { name: 'Bookmark 149', link: 'https://example.com/149' },
  { name: 'Bookmark 150', link: 'https://example.com/150' },
  { name: 'Bookmark 151', link: 'https://example.com/151' },
  { name: 'Bookmark 152', link: 'https://example.com/152' },
  { name: 'Bookmark 153', link: 'https://example.com/153' },
  { name: 'Bookmark 154', link: 'https://example.com/154' },
  { name: 'Bookmark 155', link: 'https://example.com/155' },
  { name: 'Bookmark 156', link: 'https://example.com/156' },
  { name: 'Bookmark 157', link: 'https://example.com/157' },
  { name: 'Bookmark 158', link: 'https://example.com/158' },
  { name: 'Bookmark 159', link: 'https://example.com/159' },
  { name: 'Bookmark 160', link: 'https://example.com/160' },
  { name: 'Bookmark 161', link: 'https://example.com/161' },
  { name: 'Bookmark 162', link: 'https://example.com/162' },
  { name: 'Bookmark 163', link: 'https://example.com/163' },
  { name: 'Bookmark 164', link: 'https://example.com/164' },
  { name: 'Bookmark 165', link: 'https://example.com/165' },
  { name: 'Bookmark 166', link: 'https://example.com/166' },
  { name: 'Bookmark 167', link: 'https://example.com/167' },
  { name: 'Bookmark 168', link: 'https://example.com/168' },
  { name: 'Bookmark 169', link: 'https://example.com/169' },
  { name: 'Bookmark 170', link: 'https://example.com/170' },
  { name: 'Bookmark 171', link: 'https://example.com/171' },
  { name: 'Bookmark 172', link: 'https://example.com/172' },
  { name: 'Bookmark 173', link: 'https://example.com/173' },
  { name: 'Bookmark 174', link: 'https://example.com/174' },
  { name: 'Bookmark 175', link: 'https://example.com/175' },
  { name: 'Bookmark 176', link: 'https://example.com/176' },
  { name: 'Bookmark 177', link: 'https://example.com/177' },
  { name: 'Bookmark 178', link: 'https://example.com/178' },
  { name: 'Bookmark 179', link: 'https://example.com/179' },
  { name: 'Bookmark 180', link: 'https://example.com/180' },
  { name: 'Bookmark 181', link: 'https://example.com/181' },
  { name: 'Bookmark 182', link: 'https://example.com/182' },
  { name: 'Bookmark 183', link: 'https://example.com/183' },
  { name: 'Bookmark 184', link: 'https://example.com/184' },
  { name: 'Bookmark 185', link: 'https://example.com/185' },
  { name: 'Bookmark 186', link: 'https://example.com/186' },
  { name: 'Bookmark 187', link: 'https://example.com/187' },
  { name: 'Bookmark 188', link: 'https://example.com/188' },
  { name: 'Bookmark 189', link: 'https://example.com/189' },
  { name: 'Bookmark 190', link: 'https://example.com/190' },
  { name: 'Bookmark 191', link: 'https://example.com/191' },
  { name: 'Bookmark 192', link: 'https://example.com/192' },
  { name: 'Bookmark 193', link: 'https://example.com/193' },
  { name: 'Bookmark 194', link: 'https://example.com/194' },
  { name: 'Bookmark 195', link: 'https://example.com/195' },
  { name: 'Bookmark 196', link: 'https://example.com/196' },
  { name: 'Bookmark 197', link: 'https://example.com/197' },
  { name: 'Bookmark 198', link: 'https://example.com/198' },
  { name: 'Bookmark 199', link: 'https://example.com/199' },
  { name: 'Bookmark 200', link: 'https://example.com/200' }
]);

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
