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
          { name: "Github", url: "https://github.com/ZAViking" },
          { name: "MyNinja", url: "https://myninja.ai/" },
          { name: "Python", url: "/coding/python" },
          { name: "Vue.js", url: "/coding/vue" },
          { name: "Java: Project for beginners", url:"https://www.freecodecamp.org/news/javascript-projects-for-beginners/?ref=dailydev#heading-how-to-create-a-review-carousel" },
          { name: "Automate code commenting", url:"https://blog.logrocket.com/automate-code-commenting-using-vs-code-ollama/?ref=dailydev" },
          { name: "Daily Dev", url:"https://app.daily.dev/posts/od1s1axwl" },
          { name: "VS Code: Extensions", url:"https://app.daily.dev/posts/10-vs-code-extensions-that-will-change-the-way-you-work-gnffjan60" },
          { name: "VS Code: Themes", url:"https://vscodethemes.com/?ref=dailydev)" },
          { name: "12 Logging BEST Practices in 12 minutes", url:"https://youtu.be/I2mWnh66Bkg" },
          { name: "Website Hero Section Library", url:"https://www.supahero.io/?ref=dailydev" },
          { name: "Frontend Dev: Tools", url:"https://medium.com/@hii_mohit/8-essential-tools-for-frontend-developers-in-2024-f2bdefe2f253" },
          { name: "GitHub: React Projects", url:"https://github.com/john-smilga/react-projects?tab=readme-ov-file" },
          { name: "AI: 13 Free Courses", url:"https://www.marktechpost.com/2025/01/01/13-free-ai-courses-on-ai-agents-in-2025/?ref=dailydev" },
          { name: "Tailwind Resources", url:"https://tailgrids.com/blog/tailwind-resources?ref=dailydev" },
          { name: "Security: Web Check", url:"https://github.com/Lissy93/web-check "}
        ]
    },
    { 
        name: "Gaming", 
        icon: "🎮", 
        link: "/gaming", 
        class: "gaming", 
        links: [
            { name: "GTA Cars",             url: "https://gtacars.net/gta5?page=12" },
            { name: "FiveM: Car Reference", url: "https://docs.fivem.net/docs/game-references/vehicle-models/" },
            { name: "FiveM: Car Pack",      url: "https://github.com/PLOKMJNB/FiveM-Civ-Car-Pack/tree/master" }
        ]
    },
    { 
        name: "Cooking", 
        icon: "🍳", 
        link: "/cooking", 
        class: "cooking",
        links: [
            { name: "Recipe: Today News", url: "https://todaynewsn1.net/2025/03/05/bacon-mac-n-cheese-burger-wrap/#more-1034" }
        ] 
    },
    { 
        name: "Movies", 
        icon: "🎬", 
        link: "/movies", 
        class: "movies", 
        links: [
          { name: "H!Anime", url: "https://hianime.to/watch/" }
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
        name: "Random Links", 
        icon: "🏋️", 
        link: "/randomlinks", 
        class: "hmmmm", 
        links: [
          { name: "Fallen Angels", url: "https://fallen-angels-tan.vercel.app/" }
        ] 
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
        links: [
          { name: "Plebmasters",                url: "https://forge.plebmasters.de/" },
          { name: "FiveM: Clothing Resource",   url: "https://docs.gta.clothing/getting-started/first-cloth-resource" },
          { name: "Hack: Cipher",               url: "https://cipher-panel.me/en/pricing" }
        ] 
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
