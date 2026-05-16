<template>
    <section class="relative w-full overflow-hidden min-h-screen flex items-center">
        <div class="w-full px-5 sm:px-8 md:px-12 lg:px-8 max-w-5xl lg:max-w-7xl mx-auto relative z-10">
            <div class="grid lg:grid-cols-2 gap-10 xl:gap-14 items-center">
                <!-- Left Content -->
                <div class="flex flex-col md:mt-0 mt-20 justify-center">
                    <div class="text-center lg:text-left" data-aos="fade-right">
                        <h1 class="text-white font-bold text-4xl md:text-5xl lg:text-6xl leading-tight">
                            Hi, I'm <span class="text-transparent bg-clip-text bg-linear-to-r
                             from-purple-400 to-pink-400">
                                Akshit Phonsa
                            </span> 👋
                        </h1>
                        <p class="text-purple-200 font-medium text-lg md:text-xl mt-4" 
                        data-aos="fade-right" data-aos-delay="100">
                            Full-Stack Developer | Tech Enthusiast | Problem Solver
                        </p>
                    </div>
                    <p class="text-gray-300 pt-6 text-center lg:text-left mx-auto max-w-xl text-lg leading-relaxed" data-aos="fade-right" data-aos-delay="200">
                        I craft digital solutions that combine cutting-edge technology 
                        with beautiful design. Let's turn your ideas into reality.
                    </p>
                    
                    <!-- Buttons -->
                    <div class="flex items-center gap-4 pt-8 flex-col sm:flex-row sm:w-max sm:mx-auto
                     lg:mx-0" data-aos="fade-up" data-aos-delay="300">
                        <!-- Primary Button -->
                        <button class="px-8 md:px-10 py-4 rounded-xl relative group w-full 
                        sm:w-max flex justify-center overflow-hidden
                         bg-linear-to-r from-purple-600 to-pink-600 hover:from-purple-500
                          hover:to-pink-500 transition-all duration-300">
                            <span class="relative flex items-center justify-center text-white
                             font-semibold text-lg">
                                <a href="#contact">Contact Me</a>
                                <ArrowRightIcon class="ml-2 w-5 h-5 group-hover:translate-x-1 
                                transition-transform" />
                            </span>
                        </button>

                        <!-- Secondary Button -->
                        <button class="border-2 border-purple-400 px-8 md:px-10 py-4 rounded-xl 
                        relative group w-full sm:w-max flex justify-center hover:bg-purple-400/10 
                        transition-all duration-300">
                            <div class="flex items-center justify-center relative">
                                <ArrowDownTrayIcon class="w-5 h-5 text-purple-400 group-hover:translate-y-1
                                 transition-transform" />
                                <span class="pl-3 text-purple-400 font-semibold text-lg"><a href="/public/assets/resume.pdf" target="_blank" rel="noopener noreferrer">Download CV</a></span>
                            </div>
                        </button>
                    </div>

                    <!-- Stats -->
                    <div class="flex items-center justify-center lg:justify-start gap-8 pt-12" 
                    data-aos="fade-up" data-aos-delay="400">
                        <div class="text-center">
                            <div class="text-2xl font-bold text-purple-400">30+</div>
                            <div class="text-purple-200 text-sm">Projects</div>
                        </div>
                        <div class="text-center">
                            <div class="text-2xl font-bold text-pink-400">1+</div>
                            <div class="text-pink-200 text-sm">Years</div>
                        </div>
                        <div class="text-center">
                            <div class="text-2xl font-bold text-purple-400">10+</div>
                            <div class="text-purple-200 text-sm">Clients</div>
                        </div>
                    </div>
                </div>

                <!-- Right Content - Image -->
                <div class="lg:h-full flex justify-center lg:justify-end">
                    <div class="relative w-full max-w-md lg:max-w-lg">
                      
                        <!-- Image Container -->
                        <div class="relative z-10 bg-linear-to-r from-purple-600 to-pink-600
                         rounded-[50%_40%_30%_60%/60%_30%_70%_30%]
                          p-4 backdrop-blur-sm border border-purple-500/30 shadow-2xl -translate-y-6"
                           data-aos="zoom-in" data-aos-delay="500">
                            <div class="rounded-xl overflow-hidden">
                                <img 
                                    src="../../public/assets/Akshit7.png" 
                                    alt="Mary - Full Stack Developer" 
                                    loading="lazy"
                                    class="my-10 w-[500px] h-[500px] object-contain -translate-y-8"
                                >
                            </div>
                        </div>

                        <!-- Floating Elements -->
                        <div class="absolute -top-2 -right-4 w-10 h-10 bg-purple-400 rounded-full 
                        blur-sm opacity-60 animate-pulse"></div>
                   </div>
                </div>
            </div>
        </div>

    </section>
</template>

<script setup>
import { 
    ArrowRightIcon, 
    ArrowDownTrayIcon,
    ChevronDownIcon
} from '@heroicons/vue/24/outline' 
</script>
