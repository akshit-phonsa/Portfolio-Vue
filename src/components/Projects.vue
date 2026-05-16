<template>
    <section class="relative py-20 overflow-hidden" id="projects">
        <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Section Header -->
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    My <span class="text-transparent bg-clip-text bg-linear-to-r from-purple-400
                     to-pink-400">Projects</span>
                </h2>
                <p class="text-purple-200 text-lg max-w-2xl mx-auto">
                    A collection of my recent work and creative solutions
                </p>
            </div>

            <!-- Projects Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div 
                    v-for="(project, index) in projects" 
                    :key="project.id"
                    class="group relative bg-linear-to-br from-gray-800/50 to-purple-900/30
                     rounded-3xl overflow-hidden border backdrop-blur-sm hover:border-purple-400/40
                      transition-all duration-500 hover:transform hover:-translate-y-2"
                    :class="project.borderColor"
                    data-aos="fade-up" 
                    :data-aos-delay="(index + 1) * 100"
                >
                    <!-- Project Image -->
                    <div class="relative overflow-hidden">
                        <img 
                            :src="project.image" 
                            :alt="project.title"
                            class="w-full h-48 object-cover group-hover:scale-110 transition-transform duration-500"
                        />
                        <div class="absolute inset-0 bg-linear-to-t from-gray-900 via-transparent to-transparent">

                        </div>
                        <div class="absolute top-4 right-4">
                            <span class="px-3 py-1 text-white text-xs rounded-full font-semibold" 
                                  :class="project.badgeColor">
                                {{ project.category }}
                            </span>
                        </div>
                    </div>

                    <!-- Project Content -->
                    <div class="p-6">
                        <h3 class="text-xl font-bold text-white mb-3 group-hover:text-purple-400 
                        transition-colors duration-300">
                            {{ project.title }}
                        </h3>
                        <p class="text-purple-100 text-sm leading-relaxed mb-4">
                            {{ project.description }}
                        </p>

                        <!-- Technologies -->
                        <div class="flex flex-wrap gap-2 mb-4">
                            <span 
                                v-for="tech in project.technologies" 
                                :key="tech"
                                class="px-2 py-1 border rounded text-xs"
                                :class="tech.class"
                            >
                                {{ tech.name }}
                            </span>
                        </div>

                        <!-- Project Links -->
                        <div class="flex gap-3">
                            <a 
                                v-for="link in project.links" 
                                :key="link.name"
                                :href="link.url" 
                                class="flex items-center gap-2 transition-colors duration-300 text-sm font-medium"
                                :class="link.class"
                                :target="link.url==='#' ? '_self' : '_blank'"
                                
                                rel="noopener noreferrer"
                            >
                                <component :is="link.icon" class="w-4 h-4" />
                                {{ link.name }}
                            </a>
                        </div>
                    </div>
                </div>
            </div>

            <!-- CTA Section -->
            <!-- <div class="text-center mt-16" data-aos="fade-up">
                <div class="inline-flex flex-col sm:flex-row gap-4 items-center">
                    <button class="px-8 py-4 rounded-xl bg-linear-to-r from-purple-500 to-pink-500
                     text-white font-semibold hover:shadow-lg hover:shadow-purple-500/25 transition-all
                      duration-300 hover:scale-105 flex items-center">
                        View All Projects
                        <ArrowRightIcon class="w-5 h-5 ml-2" />
                    </button>
                    <button class="px-8 py-4 rounded-xl border-2 border-purple-400 text-purple-400
                     font-semibold hover:bg-purple-400/10 transition-all duration-300 flex items-center">
                        <ChatBubbleLeftRightIcon class="w-5 h-5 mr-2" />
                        Discuss Project
                    </button>
                </div>
            </div> -->
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'
import {
    EyeIcon,
    CodeBracketIcon,
    ArrowRightIcon,
    ChatBubbleLeftRightIcon,
    PlusCircleIcon,
    ClockIcon
} from '@heroicons/vue/24/outline'

const projects = ref([
    {
        id: 1,
        title: "Uber Clone",
        description: "Developed a scalable Uber-like ride booking platform using Spring Boot, PostgreSQL/PostGIS, and strategy design patterns (driver matching & surge pricing), handling 2,000+ rides/min with 45% reduced latency and ~90% uptime under load.",
        image: "../assets/uber.png",
        category: "Backend",
        borderColor: "border-purple-500/20",
        badgeColor: "bg-purple-500",
        technologies: [
            { name: "Spring Boot", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Java", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "PostgreSQL", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "PostGIS", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" }
        ],
        links: [
            { name: "Live Demo", url: "https://drive.google.com/file/d/1Gm5h0E-Hz15k0__4FfxeL64hMuCygrjD/view?usp=sharing", icon: EyeIcon, class: "text-purple-400 hover:text-purple-300" },
            { name: "Code", url: "https://github.com/akshit-phonsa/uber-clone", icon: CodeBracketIcon, class: "text-pink-400 hover:text-pink-300" }
        ]
    },
    {
        id: 2,
        title: "Portfolio App",
        description: "Cross-platform Portfolio application with real-time collaboration and notifications.",
        image: "../assets/portfolio.png",
        category: "Frontend",
        borderColor: "border-pink-500/20",
        badgeColor: "bg-pink-500",
        technologies: [
            { name: "Vue JS", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "HTML", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "CSS", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "Tailwind CSS", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "JS", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" }
        ],
        links: [
            { name: "Live Demo", url: "#", icon: EyeIcon, class: "text-purple-400 hover:text-purple-300" },
            { name: "Code", url: "#", icon: CodeBracketIcon, class: "text-pink-400 hover:text-pink-300" }
        ]
    },
    {
        id: 3,
        title: "LinkedIn Clone",
        description: "Built a scalable LinkedIn-style social platform using Spring Boot microservices, Kafka Streams, Kubernetes, Neo4j graph modeling, and a custom UserContextHolder, supporting 10M users and 1B interactions with 65% feed optimization.",
        image: "../assets/linkedin.png",
        category: "Backend",
        borderColor: "border-purple-500/20",
        badgeColor: "bg-purple-500",
        technologies: [
            { name: "Spring Boot", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Microservices", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Neo4j", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Kafka Streams", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "Java", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" }
        ],
        links: [
            { name: "Live Demo", url: "https://www.youtube.com/watch?v=_-vb5Qo4qq4", icon: EyeIcon, class: "text-purple-400 hover:text-purple-300" },
            { name: "Code", url: "https://github.com/akshit-phonsa/linkedin-clone-local", icon: CodeBracketIcon, class: "text-pink-400 hover:text-pink-300" }
        ]
    },
    {
        id: 4,
        title: "Code Translator",
        description: "Developed an AI-powered code translator using Spring AI and React that converts code across languages while automatically fixing issues and optimizing performance.",
        image: "../assets/codeTranslator.png",
        category: "Full Stack",
        borderColor: "border-pink-500/20",
        badgeColor: "bg-pink-500",
        technologies: [
            { name: "React", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "Spring Boot", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Spring AI", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Java", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" }
        ],
        links: [
            { name: "Live Demo", url: "https://youtu.be/fIonp8MjFsc", icon: EyeIcon, class: "text-purple-400 hover:text-purple-300" },
            { name: "Code", url: "https://github.com/akshit-phonsa/CoderTranslator", icon: CodeBracketIcon, class: "text-pink-400 hover:text-pink-300" , target: "_blank"}
        ]
    },
    {
        id: 5,
        title: "iNotebook",
        description: "Built a full-stack note-taking application using React, Node.js, Express, and MongoDB with secure authentication, optimized CRUD performance, and email-based note sharing, improving user satisfaction and productivity.",
        image: "../assets/iNotebook.png",
        category: "Full Stack",
        borderColor: "border-purple-500/20",
        badgeColor: "bg-purple-500",
        technologies: [
            { name: "React", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Bootstrap", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "JavaScript", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Node.js", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "Express", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "MongoDB", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "HTML", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" },
            { name: "CSS", class: "bg-purple-500/20 border-purple-400/30 text-purple-200" }
        ],
        links: [
            { name: "Live Demo", url: "https://youtu.be/S4CQJFk9gxw", icon: EyeIcon, class: "text-purple-400 hover:text-purple-300" },
            { name: "Code", url: "https://github.com/akshit-phonsa/iNotebook", icon: CodeBracketIcon, class: "text-pink-400 hover:text-pink-300" }
        ]
    },
    {
        id: 6,
        title: "News Monkey",
        description: "Developed a responsive news web application using React, JavaScript, and Bootstrap that fetches real-time news via APIs, categorizes content (General, Sports, Entertainment), and redirects users to full articles for detailed reading.",
        image: "../assets/newsMonkey.png",
        category: "Dashboard",
        borderColor: "border-pink-500/20",
        badgeColor: "bg-pink-500",
        technologies: [
            { name: "React", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "JavaScript", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "Bootstrap", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "HTML", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" },
            { name: "CSS", class: "bg-pink-500/20 border-pink-400/30 text-pink-200" }
        ],
        links: [
            { name: "Live Demo", url: "https://youtu.be/MPrWZUODJYs", icon: EyeIcon, class: "text-purple-400 hover:text-purple-300" },
            { name: "Code", url: "https://github.com/akshit-phonsa/newsMonkey", icon: CodeBracketIcon, class: "text-pink-400 hover:text-pink-300" }
        ]
    }
])
</script>