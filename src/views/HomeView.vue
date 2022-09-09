<script setup lang="ts">
import GenericSelector from "../components/GenericSelector.vue";
import LanguageSelector from "../components/icons/LanguageSelector.vue";
interface ProgrammingLanguage {
  name: string;
  value: string;
  id: string;
  icon: string;
}

const programmingLanguages: ProgrammingLanguage[] = [
  {
    name: 'Java',
    value: 'java',
    id: 'aa92425f-5782-407a-a70f-ffaf00a3061d',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-original.svg',
  },
  {
    name: 'Python',
    value: 'python',
    id: 'bb92425f-5782-407a-a70f-ffaf00a3061d',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg',
  },
  {
    name: 'Ruby',
    value: 'ruby',
    id: 'cc92425f-5782-407a-a70f-ffaf00a3061d',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/ruby/ruby-original.svg',
  },
  {
    name: 'JavaScript',
    value: 'javascript',
    id: 'dd92425f-5782-407a-a70f-ffaf00a3061d',
    icon: 'https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg',
  }
]
</script>

<template>
  <main class="p-8">
    <div class="grid grid-cols-3 gap-8">
      <div class="px-16">
        <GenericSelector />
      </div>
      <div class="px-16">
        <LanguageSelector />
      </div>
      <div class="px-16"></div>
    </div>
  </main>
</template>
