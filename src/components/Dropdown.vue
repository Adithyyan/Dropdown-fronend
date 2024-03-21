<!-- Dropdown.vue -->
<template>
  <div>
    <header>
      <nav>
        <ul class="menu">
          <li>
              <div class="heading flex">
                <a class="green text-white font-bold w-58" href="#" @click="getPosts">
                  SHOP BY CATEGORY 
                  <i class=" arrow fa-solid fa-angle-down "></i>
                </a>
                <h1 class="offer mt-3 ml-5">
                  <i class="fa-solid fa-tag" style="color: #f41b0b;"></i>
                  OFFERS
                </h1>
              </div>
            <ul class="submenu absolute bg-white text-black text-lg left-0 hidden">
              <li v-for="category in post[0].categories" :key="category.id">
                <a href="#">{{ category.name }}</a>
                <ul class="submenu2 absolute left-full w-250 top-0 bg-white text-black text-md hidden">
                  <li v-for="subcategory in category.subcategories" :key="subcategory.id">
                    <a href="#">{{ subcategory.name }}</a>
                    <ul class="submenu3 absolute left-full w-230 top-0 bg-white text-black text-md hidden">
                        <li v-for="subsubcategory in subcategory.subcategories1" :key="subsubcategory.id">
                          <a href="#">{{ subsubcategory.name }}</a>
                        </li>
                    </ul>
                  </li>
                </ul>
              </li>
            </ul>
          </li>
        </ul>
      </nav>
    </header>
  </div>
</template>

<script>
import jsonData from '../items.json';

export default {
  methods: {
    getPosts() {
      fetch('http://localhost:8000/api/items')
        .then(response => response.json())
        .then(data => (this.post = data));
    },
  },
  mounted() {
    this.getPosts();
  },
  data() {
    return {
      post: [0],
      /* categories: jsonData.categories, */
    };
  },
};
</script>

<style scoped>
  /* Add your scoped styles here if needed */
</style>
