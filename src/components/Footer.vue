<template>
    <footer class="relative bg-gray-900/80 border-t border-purple-500/20">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
            <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                <!-- Brand -->
                <div class="md:col-span-2">
                    <div class="text-2xl font-bold bg-linear-to-r from-purple-400 to-pink-400 bg-clip-text
                     text-transparent mb-4">
                        Akshit.dev
                    </div>
                    <p class="text-purple-200 text-sm leading-relaxed max-w-md">
                        Full-Stack Developer creating digital experiences 
                        that combine innovation with elegant design.
                    </p>
                    <div class="flex gap-4 mt-6">
                        <a href="mailto:phonsaakshit@gmail.com" target="_blank" class="p-2 bg-purple-500/20 border border-purple-400/30 rounded-lg
                         text-purple-400 hover:bg-purple-500/30 transition-all">
                            <EnvelopeIcon class="w-5 h-5" />
                        </a>
                        <a href="tel:+918899021122" target="_blank" class="p-2 bg-pink-500/20 border border-pink-400/30 rounded-lg
                         text-pink-400 hover:bg-pink-500/30 transition-all">
                            <PhoneIcon class="w-5 h-5" />
                        </a>
                        <a href="https://www.google.com/maps/place/Jammu/@32.7145664,74.6951519,11z/data=!3m1!4b1!4m6!3m5!1s0x391e84bf169d3525:0xf233488eeb8fd8d!8m2!3d32.7266016!4d74.8570259!16s%2Fm%2F051zvy9?entry=ttu&g_ep=EgoyMDI2MDIwNC4wIKXMDSoKLDEwMDc5MjA2OUgBUAM%3D" target="_blank" class="p-2 bg-purple-500/20 border border-purple-400/30 rounded-lg
                         text-purple-400 hover:bg-purple-500/30 transition-all">
                            <MapPinIcon class="w-5 h-5" />
                        </a>
                        <a href="https://github.com/akshit-phonsa/" target="_blank" class="p-2 bg-purple-500/20 border border-purple-400/30 rounded-lg
                         text-purple-400 hover:bg-purple-500/30 transition-all">
                            <i class="fab fa-github w-5 h-5"></i>
                        </a>
                        <a href="https://www.linkedin.com/in/akshit-phonsa/" target="_blank" class="p-2 bg-purple-500/20 border border-purple-400/30 rounded-lg
                         text-purple-400 hover:bg-purple-500/30 transition-all">
                            <i class="fab fa-linkedin-in w-5 h-5 "></i>
                        </a>
                    </div>
                </div>

                <!-- Quick Links -->
                <div>
                    <h3 class="text-white font-semibold mb-4">Quick Links</h3>
                    <ul class="space-y-2">
                        <li v-for="link in quickLinks" :key="link.name">
                            <a :href="link.href" class="text-purple-200 hover:text-purple-400 text-sm 
                            transition-colors">
                                {{ link.name }}
                            </a>
                        </li>
                    </ul>
                </div>

                <!-- Services -->
                <div>
                    <h3 class="text-white font-semibold mb-4">Services</h3>
                    <ul class="space-y-2">
                        <li v-for="service in services" :key="service">
                            <a href="#services" class="text-purple-200 hover:text-purple-400 text-sm transition-colors">
                                {{ service }}
                            </a>
                        </li>
                    </ul>
                </div>
            </div>

            <!-- Bottom Bar -->
            <div class="border-t border-purple-500/20 mt-8 pt-8 flex flex-col md:flex-row justify-between 
            items-center">
                <p class="text-purple-300 text-sm">
                    © 2024 Akshit All rights reserved.
                </p>
                <div class="flex gap-6 mt-4 md:mt-0">
                    <a href="#" class="text-purple-300 hover:text-purple-400 text-sm transition-colors">
                        Privacy Policy
                    </a>
                    <a href="#" class="text-purple-300 hover:text-purple-400 text-sm transition-colors">
                        Terms of Service
                    </a>
                </div>
            </div>
        </div>
    </footer>
</template>

<script setup>
import { EnvelopeIcon, PhoneIcon, MapPinIcon } from '@heroicons/vue/24/outline'

const quickLinks = [
    { name: 'Home', href: '#home' },
    { name: 'About', href: '#about' },
    { name: 'Services', href: '#services' },
    { name: 'Projects', href: '#projects' },
    { name: 'Testimonials', href: '#testimonials' },
    { name: 'Contact', href: '#contact' }
]

const services = [
    'Frontend Development',
    'Backend Development',
    'Database Management',
    'Full Stack Development',
]
</script>