<template>
    <header class="flex justify-between items-center p-6 bg-opacity-50 relative z-20">

        <div class="text-3xl font-bold bg-linear-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent"> 
            Dev<span class="font-black">Portfolio</span> 
        </div>
        <!-- Mobile Toggle Button -->
        <div class="md:hidden z-30">
            <button type="button" 
                class="block focus:outline-none p-2 rounded-lg bg-purple-800/50 hover:bg-purple-700/50 
                transition-all duration-300"
                @click="isMenuOpen = !isMenuOpen"
            > 
                <div class="relative w-6 h-6">
                    <span :class="[
                        'absolute left-0 w-6 h-0.5 bg-purple-200 transition-all duration-300',
                        isMenuOpen ? 'rotate-45 top-3' : 'top-1'
                    ]"></span>
                    <span :class="[
                        'absolute left-0 w-6 h-0.5 bg-purple-200 transition-all duration-300',
                        isMenuOpen ? 'opacity-0' : 'top-3 opacity-100'
                    ]"></span>
                    <span :class="[
                        'absolute left-0 w-6 h-0.5 bg-purple-200 transition-all duration-300',
                        isMenuOpen ? '-rotate-45 top-3' : 'top-5'
                    ]"></span>
                </div>
            </button>
        </div>

        <!-- Navbar Link -->
        <nav
            :class="[`fixed inset-0 z-20 flex flex-col items-center justify-center bg-[#111827] 
            md:relative md:bg-transparent md:flex md:justify-between md:flex-row `,
            isMenuOpen ? 'block':'hidden'
            ]"
        >
            <ul class="flex flex-col items-center space-y-5 md:flex-row md:space-x-5 md:space-y-0">
                <li v-for="item in Menu" :key="item.name" class="group relative">
                    <a :href="item.href" 
                        class="relative block text-purple-100 hover:text-purple-400 transition-all 
                        duration-300 text-xl md:text-base font-medium group"
                        @click="scrollToSection(item.href)"
                    >
                        {{ item.name }}
                        <span class="absolute bottom-0 left-0 w-0 h-0.5 bg-purple-400 transition-all
                         duration-300 group-hover:w-full"></span>
                    </a>
                </li>
            </ul>
            
            <div class="mt-8 md:mt-0 md:ml-8">
                <button class="px-6 py-2.5 bg-linear-to-r from-purple-500 to-pink-500 text-white
                 rounded-full font-medium hover:shadow-lg hover:shadow-purple-500/25 transition-all
                  duration-300 hover:scale-105">
                    <a href="#contact">Let's Talk</a>
                </button>
            </div>
        </nav>
    </header>
</template>

<script setup>
import { ref } from 'vue';

const Menu = ref([
    {name:'Services', href:'#services'},
    {name:'About Me', href:'#about'},
    {name:'Skills', href:'#skills'},
    {name:'Projects', href:'#projects'},
    {name:'Certifications', href:'#certifications'},
    {name:'Testimonials', href:'#testimonials'},
    {name:'Contact', href:'#contact'},
]);

const isMenuOpen = ref(false);

const scrollToSection = (href) => {
    isMenuOpen.value = false;
    const section = document.querySelector(href);
    if(section) {
        section.scrollIntoView({behavior: 'smooth'});
    }
}
</script>