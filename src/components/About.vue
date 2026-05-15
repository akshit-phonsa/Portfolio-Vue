<template>
    <section class="relative py-20 overflow-hidden min-h-screen flex items-center" id="about">
        <div class="w-full px-5 sm:px-8 md:px-12 lg:px-8 max-w-5xl lg:max-w-7xl mx-auto relative z-10">
            <div class="grid lg:grid-cols-2 gap-10 xl:gap-14 items-center">
                
                <!-- Left Content - Images Grid -->
                <div class="lg:h-full flex justify-center lg:justify-start order-2 lg:order-1">
                    <div class="relative w-full max-w-md">
                        <div class="relative bg-linear-to-br from-gray-800/60 to-purple-900/40 
                        rounded-3xl p-6 backdrop-blur-sm border border-purple-500/30 shadow-2xl" 
                        data-aos="zoom-in">      
                            
                            <!-- Images Grid -->
                            <div class="grid grid-cols-2 gap-4">
                                <div 
                                    v-for="(image, index) in aboutImages" 
                                    :key="image.id"
                                    class="relative group"
                                    :data-aos="image.animation"
                                    :data-aos-delay="image.delay"
                                >
                                    <div class="rounded-2xl p-2 border shadow-lg" :class="image.gradient">
                                        <img 
                                            :src="image.src" 
                                            :alt="image.alt" 
                                            class="w-full h-48 object-cover rounded-xl group-hover:scale-105 
                                            transition-transform duration-300"
                                        />
                                    </div>
                                    <div class="absolute -top-2 -right-2 text-white text-xs px-2 py-1
                                     rounded-full font-semibold" :class="image.badgeColor">
                                        {{ image.badge }}
                                    </div>
                                </div>
                            </div>

                            <!-- Experience Stats Badge -->
                            <div class="absolute -bottom-4 left-1/2 transform -translate-x-1/2 z-20 
                            bg-linear-to-r from-purple-500 to-pink-500 rounded-2xl px-6 py-3 border
                             border-purple-400/40 shadow-xl" data-aos="fade-up" data-aos-delay="600">
                                <div class="text-center text-white text-xl font-bold">{{ yearOfExperience }}+ Years Experience</div>
                            </div>
                        </div>

                    </div>
                </div>

                <!-- Right Content - Text -->
                <div class="flex flex-col justify-center order-1 lg:order-2">
                    <!-- Heading -->
                    <div class="text-center lg:text-left" data-aos="fade-left">
                        <h2 class="text-white font-bold text-4xl md:text-5xl lg:text-6xl leading-tight">
                            About <span class="text-transparent bg-clip-text bg-linear-to-r from-purple-400
                             to-pink-400">Me</span>
                        </h2>
                        <p class="text-purple-200 font-medium text-lg md:text-xl mt-4" data-aos="fade-left"
                         data-aos-delay="100">
                            {{ tag }}
                        </p>
                    </div>
                    
                    <!-- Description -->
                    <p class="text-gray-300 pt-6 text-center lg:text-left text-lg leading-relaxed" 
                    data-aos="fade-left" data-aos-delay="200">
                        {{ description }}
                    </p>

                    <!-- Skills -->
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-6 pt-8" data-aos="fade-up" data-aos-delay="300">
                        <div 
                            v-for="skill in skills" 
                            :key="skill.id"
                            class="flex flex-col"
                        >
                            <div class="flex items-center gap-3 mb-3">
                                <component :is="skill.icon" class="w-6 h-6" :class="skill.iconColor" />
                                <h3 class="text-lg font-bold text-white">{{ skill.title }}</h3>
                            </div>
                            <p class="text-purple-100 text-sm">
                                {{ skill.description }}
                            </p>
                        </div>
                    </div>

                    <!-- Buttons -->
                    <div class="flex gap-4 pt-8 flex-col sm:flex-row" data-aos="fade-up" data-aos-delay="400">
                        <button 
                            v-for="button in ctaButtons" 
                            :key="button.id"
                            class="px-8 py-3 rounded-xl font-semibold transition-all duration-300 flex 
                            items-center justify-center"
                            :class="button.classes"
                        >
                            <component :is="button.icon" class="w-4 h-4" :class="button.iconClass"/>
                            <a :href="button.href">{{ button.text }}</a>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
// Import icons from Heroicons
import { 
    ArrowRightIcon,
    CodeBracketSquareIcon,
    ServerIcon,
    PaintBrushIcon,
    CubeIcon,
    ChatBubbleLeftRightIcon
} from '@heroicons/vue/24/outline'

// Import images
import about1 from '../../public/assets/About.png'
import about2 from '../../public/assets/about2.png'
import about3 from '../../public/assets/about3.png'
import about4 from '../../public/assets/about4.png'

const tag = 'Full-Stack Developer | Tech Enthusiast | Problem Solver';

const yearOfExperience = 1;

const description = `I'm a passionate full-stack developer with over ${yearOfExperience} years of experience in building dynamic and responsive web applications. I specialize in Java, Spring Boot, React, and database technologies like MySQL and MongoDB. I thrive on solving complex problems and continuously learning new technologies to create innovative solutions that make a difference.`;

// Arrays data
const aboutImages = [
    {
        id: 1,
        src: about1,
        alt: "Mary - Professional Photo",
        gradient: "bg-linear-to-r from-purple-600 to-pink-600 border-purple-400/40",
        badge: "Professional",
        badgeColor: "bg-purple-500",
        animation: "fade-right",
        delay: 200
    },
    {
        id: 2,
        src: about2,
        alt: "Mary - Working Environment",
        gradient: "bg-linear-to-r from-pink-500 to-purple-500 border-pink-400/40",
        badge: "Creative",
        badgeColor: "bg-pink-500",
        animation: "fade-left",
        delay: 300
    },
    {
        id: 3,
        src: about3,
        alt: "Mary - Coding Session",
        gradient: "bg-linear-to-r from-purple-500 to-pink-500 border-purple-400/40",
        badge: "Developer",
        badgeColor: "bg-purple-600",
        animation: "fade-right",
        delay: 400
    },
    {
        id: 4,
        src: about4,
        alt: "Mary - Design Work",
        gradient: "bg-linear-to-r from-pink-600 to-purple-600 border-pink-400/40",
        badge: "Database",
        badgeColor: "bg-pink-600",
        animation: "fade-left",
        delay: 500
    }
]

const skills = [
    {
        id: 1,
        icon: CodeBracketSquareIcon,
        iconColor: "text-purple-400",
        title: "Frontend",
        description: "Vue.js, React, Tailwind CSS, Bootstrap, HTML, CSS, Responsive Design"
    },
    {
        id: 2,
        icon: ServerIcon,
        iconColor: "text-pink-400",
        title: "Backend & Databases",
        description: "REST APIs, Spring Boot, MySQL, MongoDB, PostgreSQL, Firebase, Redis, Neo4j"
    },
    {
        id: 3,
        icon: PaintBrushIcon,
        iconColor: "text-purple-400",
        title: "Programming Languages",
        description: "Java, JavaScript, Python, C"
    },
    {
        id: 4,
        icon: CubeIcon,
        iconColor: "text-pink-400",
        title: "Tools",
        description: "Git, Docker, AWS, VSCode"
    }
]

const ctaButtons = [
    {
        id: 1,
        text: "View Portfolio",
        icon: ArrowRightIcon,
        iconClass: "ml-2 group-hover:translate-x-1 transition-transform",
        classes: "bg-linear-to-r from-purple-600 to-pink-600 text-white hover:from-purple-500 hover:to-pink-500",
        href: "#projects"
    },
    {
        id: 2,
        text: "Contact Me",
        icon: ChatBubbleLeftRightIcon,
        iconClass: "mr-2",
        classes: "border border-purple-400 text-purple-400 hover:bg-purple-400/10",
        href: "#contact"
    }
]
</script>