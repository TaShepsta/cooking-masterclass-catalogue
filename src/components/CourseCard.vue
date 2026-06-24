<!-- Script -->
<script setup>
const props = defineProps({
  course: Object,
});
const emit = defineEmits(["save-course"]);
function handleSave() {
  emit("save-course", props.course.id);
}
</script>
<!-- Template -->
<template>
  <div class="card">
    <img :src="course.image" :alt="course.title" class="card-img" />

    <div class="card-body">
      <h3>{{ course.title }}</h3>
      <p class="chef">By {{ course.chef }}</p>
      <p class="level">Level: {{ course.level }}</p>
      <p class="price">R {{ course.price.toLocaleString("en-ZA") }}</p>

      <div v-if="course.soldOut" class="sold-out">Sold Out</div>

      <button v-else @click="handleSave" :disabled="course.soldOut">
        Add to Wishlist
      </button>
    </div>
  </div>
</template>
<!-- Style -->
<style scoped>
.card {
  border: 1px solid #ddd;
  border-radius: 8px;
  overflow: hidden;
  background: white;
}
.card-img {
  width: 100%;
  height: 180px;
  object-fit: cover;
}
.card-body {
  padding: 1rem;
}
.chef {
  color: #666;
  font-size: 0.9rem;
}
.level {
  font-weight: 500;
  margin: 0.5rem 0;
}
.price {
  font-size: 1.2rem;
  font-weight: bold;
  color: #2a9d8f;
}
.sold-out {
  background: #e63946;
  color: white;
  padding: 0.5rem;
  text-align: center;
  border-radius: 4px;
  font-weight: bold;
}
button {
  width: 100%;
  padding: 0.6rem;
  background: #264653;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
button:disabled {
  background: #ccc;
  cursor: not-allowed;
}
button:hover:not(:disabled) {
  background: #2a9d8f;
}
</style>
