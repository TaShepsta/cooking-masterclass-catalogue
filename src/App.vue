<script setup>
import { ref } from 'vue'
import CourseCard from './components/CourseCard.vue'
import courses from './data/courses.js'

const wishlist = ref([]);

const toggleWishlist = (courseId) => {
  if (wishlist.value.includes(courseId)) {
    wishlist.value = wishlist.value.filter((id) => id !== courseId);
  } else {
    wishlist.value.push(courseId);
  }
};
</script>

<template>
  <header>
    <h1>Cooking Masterclass Catalogue</h1>
    <p>Learn from the best chefs' of the country</p>
    <div class="wishlist-counter">Wishlist:{{ wishlist.length }}</div>
  </header>

  <main class="catalogue">
    <CourseCard
      v-for="course in courses"
      :key="course.id"
      :course="course"
      @save-course="toggleWishlist"
    />
  </main>
</template>

<style>
body {
  font-family:
    system-ui,
    -apple-system,
    BlinkMacSystemFont,
    "Segoe UI",
    Roboto,
    Oxygen,
    Ubuntu,
    Cantarell,
    "Open Sans",
    "Helvetica Neue",
    sans-serif;
  background: #f4f1de;
  margin: 0;
}
header {
  background: #264653;
  color: white;
  padding: 1rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.wishlist-counter {
  background: #e76f51;
  padding: 0.5rem 1rem;
  border-radius: 20px;
}
.catalogue {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 1.5rem;
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
}
header {
  background: #2c5f5d;
  color: white;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
header h1 {
  margin: 0;
  font-size: 28px;
}
</style>
