<template>
    <div class="flex justify-center items-center w-full h-screen">
        <div class="w-3/12">
            <label id="listbox-label" class="block text-sm font-medium text-gray-700"> Assigned to </label>
            <div ref="menuRef" class="mt-1 relative">
                <button @focus="showDropdown = true" type="button"
                    class="relative w-full bg-white border border-gray-300 rounded-md shadow-sm pl-3 pr-10 py-2 text-left cursor-default focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500 sm:text-sm"
                    aria-haspopup="listbox" aria-expanded="true" aria-labelledby="listbox-label">
                    <span class="flex items-center">
                        <img :src="selectedLanguage?.icon" alt="" class="flex-shrink-0 h-6 w-6 rounded-full">
                        <span class="ml-3 block truncate"> {{ selectedLanguage?.name }} </span>
                    </span>
                    <span class="ml-3 absolute inset-y-0 right-0 flex items-center pr-2 pointer-events-none">
                        <svg class="h-5 w-5 text-gray-400" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"
                            fill="currentColor" aria-hidden="true">
                            <path fill-rule="evenodd"
                                d="M10 3a1 1 0 01.707.293l3 3a1 1 0 01-1.414 1.414L10 5.414 7.707 7.707a1 1 0 01-1.414-1.414l3-3A1 1 0 0110 3zm-3.707 9.293a1 1 0 011.414 0L10 14.586l2.293-2.293a1 1 0 011.414 1.414l-3 3a1 1 0 01-1.414 0l-3-3a1 1 0 010-1.414z"
                                clip-rule="evenodd" />
                        </svg>
                    </span>
                </button>
                <ul v-if="showDropdown"
                    class="absolute z-10 mt-1 w-full bg-white shadow-lg max-h-56 rounded-md py-1 text-base ring-1 ring-black ring-opacity-5 overflow-auto focus:outline-none sm:text-sm"
                    tabindex="-1" role="listbox" aria-labelledby="listbox-label"
                    aria-activedescendant="listbox-option-3">
                    <li @click.prevent="handleLanguageSelection(lang.id)" v-for="lang in programmingLanguages"
                        :key="lang.id"
                        class="text-gray-900 cursor-pointer hover:bg-slate-100 select-none relative py-2 pl-3 pr-9"
                        id="listbox-option-0" role="option">
                        <div class="flex items-center">
                            <img :src="lang.icon" alt="" class="flex-shrink-0 h-6 w-6 rounded-full">
                            <span class="font-normal ml-3 block truncate">{{ lang.name }}</span>
                        </div>

                        <span v-if="selectedLanguage?.id === lang.id"
                            class="text-indigo-600 absolute inset-y-0 right-0 flex items-center pr-4">
                            <svg class="h-5 w-5" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"
                                fill="currentColor" aria-hidden="true">
                                <path fill-rule="evenodd"
                                    d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z"
                                    clip-rule="evenodd" />
                            </svg>
                        </span>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, type Ref, onMounted, onUnmounted } from 'vue';
const menuRef: Ref = ref(null);
onMounted(() => {
    document.addEventListener('click', (event: MouseEvent) => {
        if (menuRef.value == event.target || event.composedPath().includes(menuRef.value)) {
            return;
        }

        showDropdown.value = false;
    });
})

onUnmounted(() => {
    document.removeEventListener('click', () => { });
})


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


const selectedLanguage: Ref<ProgrammingLanguage | undefined | null> = ref(programmingLanguages[0]);

const showDropdown = ref(false);

function handleLanguageSelection(id: string) {
    selectedLanguage.value = programmingLanguages.find(lang => lang.id === id);
    // showDropdown.value = false;
}
</script>

<style scoped>
</style>