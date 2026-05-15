<template>
    <section class="relative py-20 overflow-hidden" id="certifications">
        <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">

            <!-- Section Header -->
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    Certifications &amp;
                    <span class="text-transparent bg-clip-text bg-linear-to-r from-purple-400 to-pink-400">
                        Appreciation
                    </span>
                </h2>
                <p class="text-purple-200 text-lg max-w-2xl mx-auto">
                    Recognitions, achievements, and learning milestones that define my journey
                </p>
            </div>

            <!-- Tab Switcher -->
            <div class="flex justify-center mb-12" data-aos="fade-up" data-aos-delay="100">
                <div class="inline-flex p-1.5 bg-gray-800/60 backdrop-blur-sm border border-purple-500/20 rounded-2xl gap-2">
                    <button
                        @click="activeTab = 'certifications'"
                        :class="[
                            'px-6 py-2.5 rounded-xl font-semibold text-sm transition-all duration-300',
                            activeTab === 'certifications'
                                ? 'bg-linear-to-r from-purple-600 to-pink-600 text-white shadow-lg shadow-purple-500/25'
                                : 'text-purple-300 hover:text-white hover:bg-purple-500/10'
                        ]"
                    >
                        🎓 Certifications
                    </button>
                    <button
                        @click="activeTab = 'appreciation'"
                        :class="[
                            'px-6 py-2.5 rounded-xl font-semibold text-sm transition-all duration-300',
                            activeTab === 'appreciation'
                                ? 'bg-linear-to-r from-purple-600 to-pink-600 text-white shadow-lg shadow-purple-500/25'
                                : 'text-purple-300 hover:text-white hover:bg-purple-500/10'
                        ]"
                    >
                        🏆 Appreciation
                    </button>
                </div>
            </div>

            <!-- ── Certifications Tab ── -->
            <div v-if="activeTab === 'certifications'">
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div
                        v-for="(cert, index) in certificates"
                        :key="cert.id"
                        class="group relative bg-linear-to-br from-gray-800/50 to-purple-900/30 rounded-3xl overflow-hidden border border-purple-500/20 backdrop-blur-sm hover:border-purple-400/50 transition-all duration-500 hover:-translate-y-2 hover:shadow-2xl hover:shadow-purple-500/20 cursor-pointer"
                        data-aos="fade-up"
                        :data-aos-delay="(index + 1) * 100"
                        @click="openItem(cert)"
                    >
                        <!-- Thumbnail -->
                        <div class="relative h-48 overflow-hidden bg-gray-900/60">
                            <!-- Image certificates -->
                            <img
                                v-if="cert.type === 'image'"
                                :src="cert.file"
                                :alt="cert.title"
                                class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
                            />
                            <!-- PDF placeholder -->
                            <div
                                v-else-if="cert.type === 'pdf'"
                                class="w-full h-full flex flex-col items-center justify-center"
                                :class="cert.bgPlaceholder"
                            >
                                <DocumentTextIcon class="w-16 h-16 text-white/70 mb-2" />
                                <span class="text-white/60 text-xs font-medium">PDF Certificate</span>
                            </div>

                            <!-- Web / external link placeholder -->
                            <div
                                v-else
                                class="w-full h-full flex flex-col items-center justify-center"
                                :class="cert.bgPlaceholder"
                            >
                                <GlobeAltIcon class="w-16 h-16 text-white/70 mb-2" />
                                <span class="text-white/60 text-xs font-medium">Online Certificate</span>
                            </div>

                            <!-- Overlay gradient -->
                            <div class="absolute inset-0 bg-linear-to-t from-gray-900 via-transparent to-transparent opacity-60"></div>

                            <!-- Badge -->
                            <div class="absolute top-3 right-3">
                                <span class="px-3 py-1 text-xs rounded-full font-semibold text-white" :class="cert.badgeColor">
                                    {{ cert.category }}
                                </span>
                            </div>

                            <!-- Click to view hint -->
                            <div class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                                <div class="bg-purple-600/80 backdrop-blur-sm px-4 py-2 rounded-xl flex items-center gap-2">
                                    <ArrowTopRightOnSquareIcon v-if="cert.type === 'Web'" class="w-4 h-4 text-white" />
                                    <EyeIcon v-else class="w-4 h-4 text-white" />
                                    <span class="text-white text-sm font-medium">{{ cert.type === 'Web' ? 'Open Link' : 'View Certificate' }}</span>
                                </div>
                            </div>
                        </div>

                        <!-- Card Body -->
                        <div class="p-6">
                            <h3 class="text-lg font-bold text-white mb-1 group-hover:text-purple-400 transition-colors duration-300 leading-snug">
                                {{ cert.title }}
                            </h3>
                            <p class="text-purple-300 text-sm font-medium mb-2">{{ cert.issuer }}</p>
                            <div class="flex items-center gap-2 text-purple-200/60 text-xs">
                                <CalendarIcon class="w-3.5 h-3.5" />
                                {{ cert.date }}
                            </div>
                        </div>

                        <!-- Bottom glow bar -->
                        <div class="absolute bottom-0 left-0 right-0 h-0.5 bg-linear-to-r from-purple-500 to-pink-500 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                    </div>
                </div>
            </div>

            <!-- ── Appreciation Tab ── -->
            <div v-if="activeTab === 'appreciation'">
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                    <div
                        v-for="(appr, index) in appreciations"
                        :key="appr.id"
                        class="group relative bg-linear-to-br from-gray-800/50 to-purple-900/30 rounded-3xl overflow-hidden border border-pink-500/20 backdrop-blur-sm hover:border-pink-400/50 transition-all duration-500 hover:-translate-y-2 hover:shadow-2xl hover:shadow-pink-500/20 cursor-pointer"
                        data-aos="fade-up"
                        :data-aos-delay="(index + 1) * 100"
                        @click="openModal(appr)"
                    >
                        <!-- Thumbnail -->
                        <div class="relative h-48 overflow-hidden bg-gray-900/60">
                            <div
                                class="w-full h-full flex flex-col items-center justify-center"
                                :class="appr.bgPlaceholder"
                            >
                                <TrophyIcon class="w-16 h-16 text-white/70 mb-2" />
                                <span class="text-white/60 text-xs font-medium">Appreciation Certificate</span>
                            </div>
                            <div class="absolute inset-0 bg-linear-to-t from-gray-900 via-transparent to-transparent opacity-60"></div>

                            <!-- Badge -->
                            <div class="absolute top-3 right-3">
                                <span class="px-3 py-1 text-xs rounded-full font-semibold text-white bg-pink-600">
                                    Appreciation
                                </span>
                            </div>

                            <!-- Click hint -->
                            <div class="absolute inset-0 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
                                <div class="bg-pink-600/80 backdrop-blur-sm px-4 py-2 rounded-xl flex items-center gap-2">
                                    <EyeIcon class="w-4 h-4 text-white" />
                                    <span class="text-white text-sm font-medium">View Certificate</span>
                                </div>
                            </div>
                        </div>

                        <!-- Card Body -->
                        <div class="p-6">
                            <h3 class="text-lg font-bold text-white mb-1 group-hover:text-pink-400 transition-colors duration-300 leading-snug">
                                {{ appr.title }}
                            </h3>
                            <p class="text-pink-300 text-sm font-medium mb-2">{{ appr.issuer }}</p>
                            <div class="flex items-center gap-2 text-purple-200/60 text-xs">
                                <CalendarIcon class="w-3.5 h-3.5" />
                                {{ appr.date }}
                            </div>
                        </div>

                        <!-- Bottom glow bar -->
                        <div class="absolute bottom-0 left-0 right-0 h-0.5 bg-linear-to-r from-pink-500 to-purple-500 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
                    </div>
                </div>
            </div>

        </div>

        <!-- ── MODAL ── -->
        <Teleport to="body">
            <Transition name="modal">
                <div
                    v-if="modalItem"
                    class="fixed inset-0 z-50 flex items-center justify-center p-4"
                    @click.self="closeModal"
                >
                    <!-- Backdrop -->
                    <div class="absolute inset-0 bg-gray-950/80 backdrop-blur-md" @click="closeModal"></div>

                    <!-- Modal Box -->
                    <div class="relative bg-linear-to-br from-gray-800 to-purple-950 border border-purple-500/30 rounded-3xl shadow-2xl shadow-purple-500/20 max-w-3xl w-full max-h-[90vh] flex flex-col overflow-hidden">

                        <!-- Modal Header -->
                        <div class="flex items-start justify-between p-6 border-b border-purple-500/20">
                            <div>
                                <h3 class="text-xl font-bold text-white mb-1">{{ modalItem.title }}</h3>
                                <p class="text-purple-300 text-sm">{{ modalItem.issuer }} · {{ modalItem.date }}</p>
                            </div>
                            <button
                                @click="closeModal"
                                class="p-2 rounded-xl text-purple-300 hover:text-white hover:bg-purple-500/20 transition-all duration-200 ml-4 flex-shrink-0"
                            >
                                <XMarkIcon class="w-5 h-5" />
                            </button>
                        </div>

                        <!-- Modal Content -->
                        <div class="flex-1 overflow-auto p-6 flex items-center justify-center bg-gray-900/40">
                            <!-- Image preview -->
                            <img
                                v-if="modalItem.type === 'image'"
                                :src="modalItem.file"
                                :alt="modalItem.title"
                                class="max-w-full max-h-[60vh] object-contain rounded-2xl shadow-lg"
                            />
                            <!-- PDF embed -->
                            <iframe
                                v-else
                                :src="modalItem.file + '#toolbar=0'"
                                class="w-full rounded-2xl border border-purple-500/20"
                                style="height: 60vh;"
                                :title="modalItem.title"
                            ></iframe>
                        </div>

                        <!-- Modal Footer -->
                        <div class="p-4 border-t border-purple-500/20 flex justify-end gap-3">
                            <a
                                :href="modalItem.file"
                                target="_blank"
                                rel="noopener noreferrer"
                                class="flex items-center gap-2 px-5 py-2.5 rounded-xl bg-linear-to-r from-purple-600 to-pink-600 text-white text-sm font-semibold hover:from-purple-500 hover:to-pink-500 transition-all duration-300"
                            >
                                <ArrowTopRightOnSquareIcon class="w-4 h-4" />
                                Open in New Tab
                            </a>
                            <button
                                @click="closeModal"
                                class="px-5 py-2.5 rounded-xl border border-purple-400/30 text-purple-300 text-sm font-semibold hover:bg-purple-400/10 transition-all duration-300"
                            >
                                Close
                            </button>
                        </div>
                    </div>
                </div>
            </Transition>
        </Teleport>
    </section>
</template>

<script setup>
import { ref } from 'vue'
import {
    DocumentTextIcon,
    EyeIcon,
    CalendarIcon,
    XMarkIcon,
    ArrowTopRightOnSquareIcon,
    TrophyIcon,
    GlobeAltIcon
} from '@heroicons/vue/24/outline'

const activeTab = ref('certifications')
const modalItem = ref(null)

const openItem = (item) => {
    if (item.type === 'Web') {
        window.open(item.file, '_blank', 'noopener,noreferrer')
    } else {
        modalItem.value = item
    }
}
const closeModal = () => { modalItem.value = null }

// ── Certificates ──────────────────────────────────────────────────────────────
const certificates = ref([
    {
        id: 1,
        title: 'DSA with Java – Part 1',
        issuer: 'Coding Ninjas',
        date: '2023',
        category: 'DSA',
        type: 'pdf',
        file: '/assets/certificates/DSAJavaCodingNinjas.pdf',
        badgeColor: 'bg-purple-600',
        bgPlaceholder: 'bg-linear-to-br from-purple-800/60 to-pink-900/60'
    },
    {
        id: 2,
        title: 'DSA with Java – Part 2',
        issuer: 'Coding Ninjas',
        date: '2023',
        category: 'DSA',
        type: 'pdf',
        file: '/assets/certificates/DSAJavaCodingNinjas2.pdf',
        badgeColor: 'bg-purple-600',
        bgPlaceholder: 'bg-linear-to-br from-purple-900/60 to-pink-800/60'
    },
    {
        id: 3,
        title: 'Java Programming – Part 1',
        issuer: 'Coding Ninjas',
        date: '2023',
        category: 'Java',
        type: 'pdf',
        file: '/assets/certificates/JavaCodingNinjas.pdf',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    },
    {
        id: 4,
        title: 'Java Programming – Part 2',
        issuer: 'Coding Ninjas',
        date: '2023',
        category: 'Java',
        type: 'pdf',
        file: '/assets/certificates/JavaCodingNinjas2.pdf',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-900/60 to-purple-800/60'
    },
    {
        id: 5,
        title: 'Amazon Hackathon',
        issuer: 'Amazon',
        date: '2023',
        category: 'Hackathon',
        type: 'image',
        file: '/assets/certificates/AmazonHackathon.jpg',
        badgeColor: 'bg-purple-600',
        bgPlaceholder: 'bg-linear-to-br from-purple-800/60 to-pink-900/60'
    },
    {
        id: 6,
        title: 'Database Management System',
        issuer: 'Udemy',
        date: '2023',
        category: 'Database',
        type: 'image',
        file: '/assets/certificates/DBMSUdemy.jpg',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    },
    {
        id: 7,
        title: 'Flutter Development',
        issuer: 'Udemy',
        date: '2024',
        category: 'Mobile',
        type: 'image',
        file: '/assets/certificates/FlutterUdemy.jpg',
        badgeColor: 'bg-purple-600',
        bgPlaceholder: 'bg-linear-to-br from-purple-900/60 to-pink-800/60'
    },
    {
        id: 8,
        title: 'Java – Learn Tube',
        issuer: 'LearnTube',
        date: '2024',
        category: 'Java',
        type: 'image',
        file: '/assets/certificates/LearnTubeJava.png',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-900/60 to-purple-800/60'
    },
    {
        id: 9,
        title: 'Spring Boot 0 to 1',
        issuer: 'Online Course',
        date: '2024',
        category: 'Spring Boot',
        type: 'image',
        file: '/assets/certificates/SpringBoot0-1.png',
        badgeColor: 'bg-purple-600',
        bgPlaceholder: 'bg-linear-to-br from-purple-800/60 to-pink-900/60'
    },
    {
        id: 10,
        title: 'Spring Boot 1 to 100',
        issuer: 'Online Course',
        date: '2025',
        category: 'Spring Boot',
        type: 'image',
        file: '/assets/certificates/SpringBoot1-100.png',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    },
    {
        id: 11,
        title: 'Postman API Fundamentals Student Expert',
        issuer: 'Postman',
        date: '2023',
        category: 'Postman',
        type: 'Web',
        file: 'https://badges.parchment.com/public/assertions/3uIF3gwGTq-uWq33_1FVRw?identity__email=phonsaakshit@gmail.com',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    },
    {
        id: 12,
        title: 'AWS Academy Graduate - AWS Academy Introduction to Cloud Semester 1',
        issuer: 'Amazon Web Services (AWS)',
        date: '2022',
        category: 'AWS',
        type: 'Web',
        file: 'https://www.credly.com/badges/346147d8-e30b-4d0f-89d7-89b331557a88/linked_in_profile',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    },
    {
        id: 13,
        title: 'Neo4j Fundamentals',
        issuer: 'Neo4j',
        date: '2026',
        category: 'Neo4j',
        type: 'Web',
        file: 'https://graphacademy.neo4j.com/c/7fec4e99-58d8-4524-b41b-59c766149b85/',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    },
    {
        id: 14,
        title: 'Cypher Fundamentals',
        issuer: 'Neo4j',
        date: '2026',
        category: 'Neo4j',
        type: 'Web',
        file: 'https://graphacademy.neo4j.com/c/b6f2d097-f2b0-4ebf-a126-35677169b0e1/',
        badgeColor: 'bg-pink-600',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    }
])

// ── Appreciation Certificates ─────────────────────────────────────────────────
const appreciations = ref([
    {
        id: 1,
        title: 'Appreciation Certificate',
        issuer: 'North India Talent Development Team, TCS',
        date: '03-Mar-2026',
        type: 'pdf',
        file: '/assets/appreciation/Appreciation_Certificate.pdf',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    },
    {
        id: 2,
        title: 'Feedback Enthusiast Certificate',
        issuer: 'Chief Human Resource Officer, TCS',
        date: '02-Mar-2026',
        type: 'pdf',
        file: '/assets/appreciation/Appreciation_Certificate (1).pdf',
        bgPlaceholder: 'bg-linear-to-br from-purple-800/60 to-pink-900/60'
    },
    {
        id: 3,
        title: 'Appreciation Certificate',
        issuer: 'CBG Retail Americas 1 HR Team, TCS',
        date: '12-Feb-2026',
        type: 'pdf',
        file: '/assets/appreciation/Appreciation_Certificate (2).pdf',
        bgPlaceholder: 'bg-linear-to-br from-pink-900/60 to-purple-800/60'
    },
    {
        id: 4,
        title: 'Feedback Influencer Certificate',
        issuer: 'Chief Human Resource Officer, TCS',
        date: '28-Jan-2026',
        type: 'pdf',
        file: '/assets/appreciation/Appreciation_Certificate (3).pdf',
        bgPlaceholder: 'bg-linear-to-br from-purple-900/60 to-pink-800/60'
    },
    {
        id: 5,
        title: 'Feedback Enabler Certificate',
        issuer: 'Chief Human Resource Officer, TCS',
        date: '28-Jan-2026',
        type: 'pdf',
        file: '/assets/appreciation/Appreciation_Certificate (4).pdf',
        bgPlaceholder: 'bg-linear-to-br from-pink-800/60 to-purple-900/60'
    },
    {
        id: 6,
        title: 'Appreciation Certificate',
        issuer: 'CBG Retail Americas 1 ISM Team, TCS',
        date: '20-Aug-2025',
        type: 'pdf',
        file: '/assets/appreciation/Appreciation_Certificate (5).pdf',
        bgPlaceholder: 'bg-linear-to-br from-purple-800/60 to-pink-900/60'
    },
    {
        id: 7,
        title: 'On The Spot Award',
        issuer: 'Chief Human Resource Officer, TCS',
        date: '19-Mar-2026',
        type: 'pdf',
        file: '/assets/appreciation/On_The_Spot_Award.pdf',
        bgPlaceholder: 'bg-linear-to-br from-purple-800/60 to-pink-900/60'
    },
    {
        id: 8,
        title: 'On the Spot (Team) Award',
        issuer: 'Chief Human Resource Officer, TCS',
        date: '17-Jun-2025',
        type: 'pdf',
        file: '/assets/appreciation/On_the_Spot_(Team)_Award.pdf',
        bgPlaceholder: 'bg-linear-to-br from-purple-800/60 to-pink-900/60'
    }
])
</script>

<style scoped>
/* Modal transitions */
.modal-enter-active,
.modal-leave-active {
    transition: opacity 0.3s ease, transform 0.3s ease;
}
.modal-enter-from,
.modal-leave-to {
    opacity: 0;
    transform: scale(0.95);
}
</style>
