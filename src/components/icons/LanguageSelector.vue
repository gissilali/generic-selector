<template >
    <ViewlessSelector :value="language" :keyz="'id'" :options="programmingLanguages" v-slot="{
        selectedOption,
        menuRef,
        showDropdown,
        options,
        handleOptionSelection
    }">
        <div class=" flex justify-center h-full space-x-10 items-center">
            <ul>
                <li class="" @click="handleOptionSelection(language.id)" v-for="(language, index) in options"
                    :key="index">
                    <label class="py-2 px-2 block hover:bg-slate-200 mt-2  rounded-lg max-w-xs cursor-pointer"
                        :for="language.id">
                        <input v-model="selectedLanguage" type="radio" name="languages" :id="language.id"> {{
                        language.name
                        }}
                    </label>
                </li>
            </ul>
            <div class="w-24 border  h-24 shadow-sm overflow-hidden rounded-2xl">
                <img v-if="selectedOption" :src="selectedOption.icon" alt="" class="w-full h-auto" />
            </div>

        </div>
    </ViewlessSelector>
</template>
<script setup>
import ViewlessSelector from '../ViewlessSelector.vue'
import { ref } from 'vue'
const selectedLanguage = ref()

const programmingLanguages = [
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