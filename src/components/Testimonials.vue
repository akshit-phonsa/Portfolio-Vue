<template>
    <section class="relative py-20 overflow-hidden" id="testimonials">
        <div class="relative z-10 max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    Client <span class="text-transparent bg-clip-text bg-linear-to-r from-purple-400 to-pink-400">
                        Testimonials</span>
                </h2>
                <p class="text-purple-200 text-lg">What people say about working with me</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div 
                    v-for="(testimonial, index) in testimonials" 
                    :key="testimonial.id"
                    class="bg-linear-to-br from-gray-800/50 to-purple-900/30 rounded-2xl p-6 border
                     border-purple-500/20 backdrop-blur-sm hover:border-purple-400 transition-all duration-300"
                    data-aos="fade-up"
                    :data-aos-delay="index * 100"
                >
                    <!-- Rating -->
                    <div class="flex gap-1 mb-4">
                        <StarIcon class="w-5 h-5 text-pink-400" v-for="n in 5" :key="n" />
                    </div>

                    <!-- Testimonial Text -->
                    <p class="text-purple-100 text-sm leading-relaxed mb-6">
                        "{{ testimonial.text }}"
                    </p>

                    <!-- Client Info -->
                    <div class="flex items-center gap-4">
                        <div class="w-12 h-12 rounded-full overflow-hidden border-2 border-purple-400/50">
                            <img 
                                :src="testimonial.avatar" 
                                :alt="testimonial.name"
                                class="w-full h-full object-cover"
                            />
                        </div>
                        <div>
                            <p class="text-white font-semibold">{{ testimonial.name }}</p>
                            <p class="text-purple-300 text-sm">{{ testimonial.position }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { StarIcon } from '@heroicons/vue/24/solid'

// استيراد الصور
// Public folder assets — referenced as URL strings (not imported as modules)
const person1 = '/assets/person1.png'
const person2 = '/assets/person2.png'
const person3 = '/assets/person3.png'

const testimonials = [
    {
        id: 1,
        text: "As a Product Owner at TCS, I had the opportunity to work closely with Akshit on multiple full-stack development initiatives. He consistently delivered high-quality solutions, demonstrated strong ownership of backend and frontend tasks, and showed excellent problem-solving skills. His ability to translate business requirements into scalable technical implementations made him a dependable member of the team.",
        name: "Palak Bichpuria",
        position: "Product Owner",
        avatar: person1
    },
    {
        id: 2,
        text: "Working with Akshit was a great experience — he consistently delivered high-quality web solutions with attention to performance and user experience. His technical depth and problem-solving mindset helped streamline several development workflows.",
        name: "Andres Ballon Delgado",
        position: 'Client Manager',
        avatar: person2
    },
    {
        id: 3,
        text: "As Managing Director at Pinnacleway Solutions, I observed Akshit’s strong technical capabilities and dedication to delivering reliable software solutions. He approaches development with precision, maintains clean coding practices, and collaborates effectively with stakeholders, making him a valuable asset for any full-stack project.",
        name: "Gourango Singha",
        position: "Managing Director, Pinnacleway Solutions",
        avatar: person3
    }
]
</script>