<script setup>
const categories = [
  { name: "Coding", icon: "💻", link: "/coding", class: "coding" },
  { name: "Gaming", icon: "🎮", link: "/gaming", class: "gaming" },
  { name: "Cooking", icon: "🍳", link: "/cooking", class: "cooking" },
  { name: "Movies", icon: "🎬", link: "/movies", class: "movies" },
  { name: "Music", icon: "🎵", link: "/music", class: "music" },
  { name: "Fitness", icon: "🏋️", link: "/fitness", class: "fitness" },
  { name: "Travel", icon: "✈️", link: "/travel", class: "travel" },
  { name: "Tech", icon: "🔧", link: "/tech", class: "tech" },
  { name: "Books", icon: "📚", link: "/books", class: "books" }
]
</script>

<template>
  <div class="grid-container">
    <NuxtLink 
      v-for="category in categories" 
      :key="category.name" 
      :to="category.link"
      class="block"
      :class="category.class"
    >
      <div class="block-icon">{{ category.icon }}</div>
    </NuxtLink>
  </div>
</template>
