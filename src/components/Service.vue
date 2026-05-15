<template>
    <section class="relative py-20 overflow-hidden" id="services">
        <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Section Header -->
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    My <span class="text-transparent bg-clip-text bg-linear-to-r from-purple-400 to-pink-400">
                        Services
                    </span> 
                </h2>
                <p class="text-purple-200 text-lg max-w-2xl mx-auto" data-aos="fade-up" data-aos-delay="100">
                    Comprehensive digital solutions tailored to your business needs
                </p>
            </div> 
            <!-- Services Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <div 
                    v-for="(service, index) in services" 
                    :key="service.id" 
                    :data-aos="'fade-up'"
                    :data-aos-delay="(index * 100) + 200"
                    class="group relative p-8 rounded-2xl bg-linear-to-br from-gray-800/50
                     to-purple-900/30 backdrop-blur-sm border border-purple-500/20 hover:border-purple-400/40
                      transition-all duration-500 hover:transform hover:-translate-y-2"
                >
                    <!-- Hover Effect Background -->
                    <div class="absolute inset-0 bg-linear-to-r from-purple-500/5 to-pink-500/5
                     rounded-2xl opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>
                    
                    <!-- Icon Container -->
                    <div class="relative z-10 mb-6">
                        <div class="inline-flex items-center justify-center w-16 h-16 rounded-xl
                         bg-linear-to-r from-purple-500/20 to-pink-500/20 border border-purple-400/30
                          group-hover:scale-110 transition-transform duration-300">
                            <component :is="service.icon" class="w-8 h-8 text-purple-400" />
                        </div>
                    </div>

                    <!-- Content -->
                    <div class="relative z-10">
                        <h3 class="text-xl font-bold text-white mb-3 group-hover:text-purple-400 
                        transition-colors duration-300">
                            {{ service.name }}
                        </h3>
                        <p class="text-purple-100 leading-relaxed">
                            {{ service.description }}
                        </p>
                    </div>

                    <!-- Hover Arrow -->
                    <!-- <div class="absolute bottom-6 right-6 opacity-0 group-hover:opacity-100 transform
                     translate-x-4 group-hover:translate-x-0 transition-all duration-300">
                        <ArrowRightIcon class="w-6 h-6 text-pink-400" />
                    </div> -->
                </div>
            </div>

            <!-- CTA Section -->
            <div class="text-center mt-16" data-aos="fade-up" data-aos-delay="800">
                <div class="inline-flex flex-col sm:flex-row gap-4 items-center">
                    <button class="px-8 py-4 rounded-xl bg-linear-to-r from-purple-500 to-pink-500
                     text-white font-semibold hover:shadow-lg hover:shadow-purple-500/25 transition-all
                      duration-300 hover:scale-105 flex items-center">
                        <a href="#projects">View All Projects</a>
                        <ArrowRightIcon class="w-5 h-5 ml-2" />
                    </button>
                    <button class="px-8 py-4 rounded-xl border-2 border-purple-400 text-purple-400
                     font-semibold hover:bg-purple-400/10 transition-all duration-300 flex items-center">
                        <a href="#contact">Get In Touch</a>
                        <ChatBubbleLeftRightIcon class="w-5 h-5 ml-2" />
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue';
import { 
    ArrowRightIcon,
    ChatBubbleLeftRightIcon,
    ComputerDesktopIcon,
    ServerIcon,
    CircleStackIcon,
    Squares2X2Icon,
    BoltIcon,
    CloudIcon,
} from '@heroicons/vue/24/outline';

const services = ref([
    {
        id: 1,
        icon: ComputerDesktopIcon,
        name: 'Frontend Development',
        description: 'Building responsive and interactive user interfaces using modern frameworks like React or Vue.js.'
    },
    {
        id: 2,
        icon: ServerIcon,
        name: 'Backend API Development',
        description: 'Designing scalable RESTful or microservice-based APIs using Spring Boot or similar technologies.'
    },
    {
        id: 3,
        icon: CircleStackIcon,
        name: 'Database Design & Optimization',
        description: 'Creating efficient database schemas and optimizing queries for performance using SQL or NoSQL databases.'
    },
    {
        id: 4,
        icon: Squares2X2Icon,
        name: 'Full Stack Web Application Development',
        description: 'Developing complete end-to-end web applications from UI to backend logic and deployment.'
    },
    {
        id: 5,
        icon: BoltIcon,
        name: 'Performance Optimization & Debugging',
        description: 'Improving application speed, fixing bottlenecks, and resolving technical issues across the stack.'
    },
    {
        id: 6,
        icon: CloudIcon,
        name: 'Cloud Deployment & DevOps Integration',
        description: 'Deploying applications using Docker, CI/CD pipelines, and cloud platforms for scalability and reliability'
    },
])
</script>