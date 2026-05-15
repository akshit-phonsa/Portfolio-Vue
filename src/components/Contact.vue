<template>
    <section class="relative py-20 overflow-hidden" id="contact">
        <div class="relative z-10 max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="text-center mb-16" data-aos="fade-up">
                <h2 class="text-4xl md:text-5xl font-bold text-white mb-4">
                    Get In <span class="text-transparent bg-clip-text bg-linear-to-r from-purple-400 to-pink-400">
                        Touch</span>
                </h2>
                <p class="text-purple-200 text-lg">Let's work together on your next project</p>
            </div>

            <div class="grid lg:grid-cols-2 gap-12">
                <!-- Contact Info -->
                <div data-aos="fade-right">
                    <h3 class="text-2xl font-bold text-white mb-6">Contact Information</h3>
                    
                    <div class="space-y-6">
                        <div class="flex items-center gap-4">
                            <EnvelopeIcon class="w-6 h-6 text-purple-400" />
                            <div>
                                <p class="text-white font-semibold">Email</p>
                                <p class="text-purple-200">phonsaakshit@gmail.com</p>
                            </div>
                        </div>
                        
                        <div class="flex items-center gap-4">
                            <PhoneIcon class="w-6 h-6 text-pink-400" />
                            <div>
                                <p class="text-white font-semibold">Phone</p>
                                <p class="text-purple-200">+91 8899021122</p>
                            </div>
                        </div>
                        
                        <div class="flex items-center gap-4">
                            <MapPinIcon class="w-6 h-6 text-purple-400" />
                            <div>
                                <p class="text-white font-semibold">Location</p>
                                <p class="text-purple-200">Jammu, Jammu and Kashmir, India</p>
                            </div>
                        </div>
                    </div>

                    <!-- Social Links -->
                    <div class="mt-8">
                        <h4 class="text-lg font-bold text-white mb-4">Follow Me</h4>
                        <div class="flex gap-4">
                            <a href="https://github.com/akshit-phonsa/" target="_blank" class="p-3 bg-purple-500/20 border border-purple-400/30 rounded-xl
                             text-purple-400 hover:bg-purple-500/30 transition-all">
                                <i class="w-5 h-5 fab fa-github" ></i>
                            </a>
                            <a href="https://www.linkedin.com/in/akshit-phonsa/" target="_blank" class="p-3 bg-pink-500/20 border border-pink-400/30 rounded-xl
                             text-pink-400 hover:bg-pink-500/30 transition-all">
                                <i class="w-5 h-5 fab fa-linkedin" ></i>
                            </a>
                            <a href="#" class="p-3 bg-purple-500/20 border border-purple-400/30 rounded-xl
                             text-purple-400 hover:bg-purple-500/30 transition-all" @click.prevent="shareProfile">
                                <ShareIcon class="w-5 h-5" />
                            </a>
                        </div>
                    </div>
                </div>

                <!-- Contact Form -->
                <div data-aos="fade-left">
                    <form @submit.prevent="sendEmail" class="space-y-6">
                        <div class="grid sm:grid-cols-2 gap-6">
                            <div>
                                <label class="text-white text-sm font-medium mb-2 block">Name</label>
                                <input v-model="form.name" type="text" class="w-full bg-gray-800/50 border border-purple-500/30 
                                rounded-xl px-4 py-3 text-white placeholder-purple-300 focus:border-purple-400 
                                focus:outline-none transition-all">
                            </div>
                            <div>
                                <label class="text-white text-sm font-medium mb-2 block">Email</label>
                                <input v-model="form.email" type="email" class="w-full bg-gray-800/50 border border-purple-500/30
                                 rounded-xl px-4 py-3 text-white placeholder-purple-300 focus:border-purple-400
                                  focus:outline-none transition-all">
                            </div>
                        </div>
                        
                        <div>
                            <label class="text-white text-sm font-medium mb-2 block">Subject</label>
                            <input v-model="form.subject" type="text" class="w-full bg-gray-800/50 border border-purple-500/30
                             rounded-xl px-4 py-3 text-white placeholder-purple-300 focus:border-purple-400
                              focus:outline-none transition-all">
                        </div>
                        
                        <div>
                            <label class="text-white text-sm font-medium mb-2 block">Message</label>
                            <textarea v-model="form.message" rows="4" class="w-full bg-gray-800/50 border border-purple-500/30 
                            rounded-xl px-4 py-3 text-white placeholder-purple-300 focus:border-purple-400 
                            focus:outline-none transition-all"></textarea>
                        </div>
                        
                        <button type="submit" class="w-full bg-linear-to-r from-purple-500 to-pink-500
                         text-white font-semibold py-3 rounded-xl hover:shadow-lg hover:shadow-purple-500/25
                          transition-all duration-300">
                            Send Message
                        </button>
                    </form>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
import { 
    EnvelopeIcon,
    PhoneIcon,
    MapPinIcon,
    ShareIcon
} from '@heroicons/vue/24/outline'
import { ref } from 'vue'
import emailjs from "@emailjs/browser"

const form = ref({
  name: "",
  email: "",
  subject: "",
  message: ""
})

const clearForm = () => {
  form.value.name = ""
  form.value.email = ""
  form.value.subject = ""
  form.value.message = ""
}

const sendEmail = () => {

  emailjs.send(
    "service_gzteoc7",
    "template_ggy80im",
    {
      from_name: form.value.name,
      from_email: form.value.email,
      subject: form.value.subject,
      message: form.value.message
    },
    "-WMc5C05xxofeFTFc"
  )
  .then(() => {
    alert("Message sent successfully!")
    clearForm()
  })
  .catch((error) => {
    console.log(error)
  })
}

function shareProfile() {
    if (navigator.share) {
      navigator.share({
        title: 'Akshit Phonsa Portfolio',
        text: 'Check my profile',
        url: window.location.href
      });
    }
  }
</script>