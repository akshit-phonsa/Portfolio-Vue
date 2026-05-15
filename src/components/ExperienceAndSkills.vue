<template>
    <section class="relative py-20 overflow-hidden" id="skills">
        <div class="relative z-10 max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <!-- Section Header -->
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    <span class="text-transparent bg-clip-text bg-linear-to-r from-purple-400 to-pink-400">
                        Skills
                    </span> & Experience
                </h2>
                <p class="text-purple-200 text-lg max-w-2xl mx-auto">
                    My technical expertise and professional journey
                </p>
            </div>

            <div class="grid lg:grid-cols-2 gap-12 lg:gap-16">
                <!-- Skills Section -->
                <div data-aos="fade-right">
                    <h3 class="text-2xl font-bold text-white mb-8 flex items-center gap-3">
                        <CpuChipIcon class="w-8 h-8 text-purple-400" />
                        Technical Skills
                    </h3>

                    <div class="space-y-6">
                        <div 
                            v-for="skill in skills" 
                            :key="skill.id"
                            class="group"
                        >
                            <div class="flex items-center justify-between mb-3">
                                <span class="text-purple-200 font-semibold flex items-center gap-2">
                                    <component :is="skill.icon" class="w-5 h-5" :class="skill.iconColor" />
                                    {{ skill.title }}
                                </span>
                                <span :class="skill.percentageColor">{{ skill.percentage }}%</span>
                            </div>
                            <div class="h-2 bg-gray-700 rounded-full overflow-hidden">
                                <div 
                                    class="h-full rounded-full transition-all duration-1000 group-hover:scale-105" 
                                    :class="skill.gradient"
                                    :style="{ width: skill.percentage + '%' }"
                                ></div>
                            </div>
                        </div>
                    </div>

                    <!-- Tech Stack -->
                    <div class="mt-12">
                        <h4 class="text-xl font-bold text-white mb-6 flex items-center gap-2">
                            <Squares2X2Icon class="w-6 h-6 text-pink-400" />
                            Tech Stack
                        </h4>
                        <div class="flex flex-wrap gap-3">
                            <span 
                                v-for="tech in techStack" 
                                :key="tech" 
                                class="px-4 py-2 bg-linear-to-r from-purple-500/20 to-pink-500/20 border
                                 border-purple-400/30 rounded-full text-purple-200 text-sm font-medium
                                  hover:scale-105 transition-transform duration-300"
                            >
                                {{ tech }}
                            </span>
                        </div>
                    </div>
                </div>

                <!-- Experience Section -->
                <div data-aos="fade-left">
                    <h3 class="text-2xl font-bold text-white mb-8 flex items-center gap-3">
                        <BriefcaseIcon class="w-8 h-8 text-pink-400" />
                        Work Experience
                    </h3>

                    <div class="space-y-8">
                        <div 
                            v-for="exp in experiences" 
                            :key="exp.id"
                            class="relative pl-8 border-l-2 group"
                            :class="exp.borderColor"
                        >
                            <div 
                                class="absolute -left-2 top-0 w-4 h-4 rounded-full group-hover:scale-150 
                                transition-transform duration-300"
                                :class="exp.dotColor"
                            ></div>
                            <div 
                                class="bg-linear-to-br from-gray-800/50 to-purple-900/30 rounded-2xl p-6
                                 border backdrop-blur-sm group-hover:border-purple-400/40 transition-all
                                  duration-300"
                                :class="exp.borderClass"
                            >
                                <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between mb-3">
                                    <h4 class="text-lg font-bold text-white">{{ exp.position }}</h4>
                                    <span :class="exp.dateColor" class="mt-1 sm:mt-0">{{ exp.period }}</span>
                                </div>
                                <p :class="exp.companyColor" class="font-medium mb-3">{{ exp.company }}</p>
                                <p class="text-purple-100 text-sm leading-relaxed">{{ exp.description }}</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import {
    CpuChipIcon,
    CodeBracketIcon,
    ServerIcon,
    PaintBrushIcon,
    DevicePhoneMobileIcon,
    CloudIcon,
    Squares2X2Icon,
    BriefcaseIcon
} from '@heroicons/vue/24/outline'

// Skills Data
const skills = [
    {
        id: 1,
        title: "Frontend Development",
        icon: CodeBracketIcon,
        iconColor: "text-purple-400",
        percentage: 90,
        percentageColor: "text-purple-400 text-sm",
        gradient: "bg-linear-to-r from-purple-500 to-pink-500"
    },
    {
        id: 2,
        title: "Backend Development",
        icon: ServerIcon,
        iconColor: "text-pink-400",
        percentage: 85,
        percentageColor: "text-pink-400 text-sm",
        gradient: "bg-linear-to-r from-pink-500 to-purple-500"
    },
    {
        id: 3,
        title: "Database Management",
        icon: PaintBrushIcon,
        iconColor: "text-purple-400",
        percentage: 88,
        percentageColor: "text-purple-400 text-sm",
        gradient: "bg-linear-to-r from-purple-500 to-pink-500"
    },
    {
        id: 4,
        title: "Mobile Development",
        icon: DevicePhoneMobileIcon,
        iconColor: "text-pink-400",
        percentage: 80,
        percentageColor: "text-pink-400 text-sm",
        gradient: "bg-linear-to-r from-pink-500 to-purple-500"
    },
    {
        id: 5,
        title: "DevOps & Cloud",
        icon: CloudIcon,
        iconColor: "text-purple-400",
        percentage: 50,
        percentageColor: "text-purple-400 text-sm",
        gradient: "bg-linear-to-r from-purple-500 to-pink-500"
    }
]

// Experiences Data
const experiences = [
    {
        id: 1,
        position: "System Engineer",
        company: "Tata Consultancy Services",
        period: "Nov 2024 - Present",
        description: "Built and maintained scalable backend services for a nationwide high-traffic Canadian pharmacy platform using Spring Boot, RESTful APIs, concurrency control, and optimized MySQL data architecture.",
        borderColor: "border-pink-500/30",
        dotColor: "bg-pink-500",
        borderClass: "border-pink-500/20",
        dateColor: "text-pink-400 text-sm font-semibold",
        companyColor: "text-purple-400"
    },
    {
        id: 2,
        position: "Software Developer Intern",
        company: "Pinnacleways Solutions Pvt. Ltd.",
        period: "Jan 2024 - June 2024",
        description: "Developed and deployed a responsive, client-centric web platform using PHP, MySQL, and customized UI themes, while contributing to backend logic and IoT-focused research initiatives.",
        borderColor: "border-purple-500/30",
        dotColor: "bg-purple-500",
        borderClass: "border-purple-500/20",
        dateColor: "text-purple-400 text-sm font-semibold",
        companyColor: "text-pink-400"
    }
]

const techStack = [
    'Vue.js', 'React', 'Spring Boot', 'Java', 'JavaScript', 'Python', 'C', 'MySQL',
    'MongoDB', 'PostgreSQL', 'Tailwind CSS', 'AWS',
    'Docker', 'Git', 'REST APIs', 'Bootstrap', 'Responsive Design'
]
</script>