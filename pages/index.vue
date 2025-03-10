<script setup lang="ts">
import { ref } from 'vue'

const isOpen = ref(false)
const selectedCategory = ref<{ name: string; links: { name: string; url: string }[] } | null>(null)

const categories = [
    { 
        name: "Coding", 
        icon: "💻", 
        link: "/coding", 
        class: "coding", 
        links: [
        { name: "JavaScript", url: "/coding/javascript" },
        { name: "Python", url: "/coding/python" },
        { name: "Vue.js", url: "/coding/vue" }
        ]
    },
    { 
        name: "Gaming", 
        icon: "🎮", 
        link: "/gaming", 
        class: "gaming", 
        links: [
            { name: "PC Games", url: "/gaming/pc" },
            { name: "Console Games", url: "/gaming/console" }
        ]
    },
    { 
        name: "Cooking", 
        icon: "🍳", 
        link: "/cooking", 
        class: "cooking",
        links: [
            { name: "Cooking 1", url: "/gaming/pc" },
            { name: "Cooking 2", url: "/gaming/console" }
        ] 
    },
    { 
        name: "Movies", 
        icon: "🎬", 
        link: "/movies", 
        class: "movies", 
        links: [
            
        ] 
    },
    { 
        name: "Music", 
        icon: "🎵", 
        link: "/music", 
        class: "music", 
        links: [
            { name: "Spotify", url: "https://open.spotify.com" }
        ] 
    },
    { 
        name: "Fitness", 
        icon: "🏋️", 
        link: "/fitness", 
        class: "fitness", 
        links: [] 
    },
    { 
        name: "Travel", 
        icon: "✈️", 
        link: "/travel", 
        class: "travel", 
        links: [] 
    },
    { 
        name: "Tech", 
        icon: "🔧", 
        link: "/tech", 
        class: "tech", 
        links: [] 
    },
    { 
        name: "Books", 
        icon: "📚", 
        link: "/books", 
        class: "books", 
        links: [] 
    }
]

const openSlideover = (category: typeof categories[number]) => {
  selectedCategory.value = category
  isOpen.value = true
}
</script>

<template>
  <div class="grid-container">
    <div 
      v-for="category in categories" 
      :key="category.name" 
      class="block"
      :class="category.class"
      @click="openSlideover(category)"
    >
      <div class="block-icon">{{ category.icon }}</div>
    </div>
</div>

<USlideover v-model="isOpen" class="slideover-custom">
    <UCard class="u-card">
        <template #header>
        <h2 class="text-lg font-bold">{{ selectedCategory?.icon }} {{ selectedCategory?.name || 'Category' }}</h2>
      </template>
  
      <div v-if="selectedCategory">
        <ul>
          <li v-for="link in selectedCategory.links" :key="link.url">
            <NuxtLink :to="link.url" target="_blank" >{{ link.name }}</NuxtLink>
          </li>
        </ul>
      </div>
  
      <template #footer>
        <UButton label="Close" class="bg-gray-800 text-white hover:bg-gray-600 w-full" @click="isOpen = false" />
      </template>
    </UCard>
  </USlideover>
</template>
