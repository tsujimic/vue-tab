<script setup lang="ts">
import { ref } from 'vue'
import Home from './items/Home.vue'
import Posts from './items/Posts.vue'
import Archive from './items/Archive.vue'
 
const currentTab = ref(0)

const tabs = [
  { name: '#1 Home', component: Home } ,
  { name: '#2 Posts', component: Posts } ,
  { name: '#3 Archive', component: Archive } ,
]

</script>

<template>
    <header class="bg-white shadow">
        <div class="mx-auto max-w-7xl py-2 px-3 sm:px-6 lg:px-8">
          <h1 class="text-2xl font-bold tracking-tight text-gray-900">Tab</h1>
        </div>
    </header>
    <main>
        <div class="demo">
            <button
                v-for="(tab, index) in tabs"
                :key="index"
                :class="['tab-button', { active: currentTab === index }]"
                @click="currentTab = index"
            >
            {{ tab.name }}
            </button>
            <KeepAlive>
                <component :is="tabs[currentTab].component" class="tab" :msg="tabs[currentTab].name"></component>
            </KeepAlive>
        </div>

    </main>    
</template>
    
<style scoped>
.demo {
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 40px;
  user-select: none;
  overflow-x: auto;
}

.tab-button {
  padding: 6px 10px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border: 1px solid #ccc;
  cursor: pointer;
  background: #f0f0f0;
  margin-bottom: -1px;
  margin-right: -1px;
  font-size: small;
}
.tab-button:hover {
  background: #e0e0e0;
}
.tab-button.active {
  background: #e0e0e0;
}
.tab {
  border: 1px solid #ccc;
  padding: 10px;
}
</style>
    