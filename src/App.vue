<script setup>
import { onMounted } from 'vue'
import {
  ChartBarIcon,
  BoltIcon,
  CubeIcon,
  CheckCircleIcon
} from '@heroicons/vue/24/outline' // use outline for a clean bordered look
import { ArrowDownIcon } from '@heroicons/vue/24/solid'
import { PhoneIcon, DevicePhoneMobileIcon } from '@heroicons/vue/24/solid'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
import { ref } from 'vue'

const faqs = ref([
  {
    question: 'Is this suitable for someone without coding knowledge?',
    answer: 'Absolutely! Our service is fully managed. You focus on your business—we’ll handle the tech.',
    open: false
  },
  {
    question: 'How long does it take to get my eShop live?',
    answer: 'Most websites are delivered in under 5 days, ready to accept orders immediately.',
    open: false
  },
  {
    question: 'Can I connect my Instagram products?',
    answer: 'Yes! We specialize in converting your Instagram catalog into a high-converting storefront.',
    open: false
  },
  {
    question: 'Will I be able to manage the site myself?',
    answer: 'Yes, the admin dashboard is simple and built for non-technical users to update products, track orders, and run promotions.',
    open: false
  }
])
const showContact = ref(true)

function toggleFAQ(index) {
  faqs.value[index].open = !faqs.value[index].open
}

gsap.registerPlugin(ScrollTrigger)

function scrollToFeatures() {
  const el = document.getElementById('features')
  el && el.scrollIntoView({ behavior: 'smooth' })
}
// function beforeEnter(el) {
//   el.style.maxHeight = '0px'
//   el.style.opacity = '0'
//   el.style.overflow = 'hidden'
// }

// function enter(el) {
//   el.style.transition = 'max-height 0.3s ease, opacity 0.3s ease'
//   el.style.maxHeight = '300px' // Large enough for all FAQ answers
//   el.style.opacity = '1'
// }

// function leave(el) {
//   el.style.transition = 'max-height 0.3s ease, opacity 0.3s ease'
//   el.style.maxHeight = '0px'
//   el.style.opacity = '0'
// }
onMounted(() => {
  gsap.from('.scroll-down-icon', {
    y: -10,
    repeat: -1,
    yoyo: true,
    duration: 0.8,
    ease: 'power1.inOut'
  })

  gsap.from('#features', {
    opacity: 0,
    y: 100,
    duration: 1,
    scrollTrigger: {
      trigger: '#features',
      start: 'top 85%',
    }
  })

  gsap.from('.feature-card', {
    opacity: 0,
    y: 50,
    duration: 1,
    stagger: 0.2,
    scrollTrigger: {
      trigger: '#features',
      start: 'top 90%',
    }
  })

  gsap.from('.owner-text', {
    opacity: 0,
    x: -100,
    duration: 1,
    scrollTrigger: {
      trigger: '.owner-text',
      start: 'top 95%',
    }
  })

  gsap.from('.owner-image', {
    opacity: 0,
    x: 100,
    duration: 1,
    scrollTrigger: {
      trigger: '.owner-image',
      start: 'top 95%',
    }
  })

  gsap.from('.client-text', {
    opacity: 0,
    x: 100,
    duration: 1,
    scrollTrigger: {
      trigger: '.client-text',
      start: 'top 97%',
    }
  })

  gsap.from('.client-image', {
    opacity: 0,
    x: -100,
    duration: 1,
    scrollTrigger: {
      trigger: '.client-image',
      start: 'top 97%',
    }
  })
  // FAQ Section Animation
    gsap.from('.faq-section', {
    opacity: 0,
    y: 80,
    duration: 1,
    scrollTrigger: {
        trigger: '.faq-section',
        start: 'top 90%',
    }
    })

    // CTA Section Animation
    gsap.from('.cta-section', {
    opacity: 0,
    y: 80,
    duration: 1,
    scrollTrigger: {
        trigger: '.cta-section',
        start: 'top 90%',
    }
    })
})
</script>

<template>
  <main class="bg-white text-gray-900 scroll-smooth">
    <!-- Hero -->
    <header class="relative overflow-hidden bg-white">
    <!-- Brand Top Bar -->
    <div class="relative z-20 flex items-center justify-between px-8 md:px-16 py-4">
    <span class="text-xl font-bold text-gray-900 tracking-tight">
    Opti<span class="text-blue-600">vance</span>
    </span>

    </div>

      <div class="absolute inset-0 z-0">
        <img src="./assets/waves.svg" class="w-full h-full object-cover opacity-10" alt="Decorative background" />
      </div>
      <div class="absolute -top-20 -left-20 w-96 h-96 bg-blue-300 rounded-full mix-blend-multiply filter blur-3xl opacity-30 z-0"></div>

      <div class="relative z-10 grid grid-cols-1 md:grid-cols-2 items-center gap-8 p-8 md:p-16">
        <section class="flex justify-center md:justify-end">
          <img src="./assets/example-shop.jpeg" alt="Example eShop preview"
            class="w-full max-w-md rounded-3xl shadow-2xl object-cover transition-transform duration-500 hover:scale-105">
        </section>

        <section class="flex flex-col gap-6">
          <h1 class="text-4xl md:text-5xl font-extrabold leading-tight">
            <span>Make Your </span>
            <span class="text-blue-600">Online Presence</span>
            <span> Unforgettable</span>
          </h1>
          <p class="text-lg text-gray-500 max-w-md">
            Get a tailor-made eShop website delivered in record time, optimized for speed and designed to convert your Instagram followers into loyal customers.
          </p>
          <button @click="scrollToFeatures"
            class="inline-flex items-center gap-2 px-6 py-3 text-white bg-blue-600 hover:bg-blue-700 transition rounded-lg text-lg font-semibold shadow-md">
            See Features
            <ArrowDownIcon class="w-5 h-5 scroll-down-icon" />
          </button>
        </section>
      </div>
    </header>

    <!-- Features Section -->
    <section id="features" class="relative py-24 px-8 md:px-16 bg-white overflow-visible">
    <!-- Top Fade Background -->
    <div class="absolute top-0 left-0 w-full h-24 bg-gradient-to-b from-blue-100 to-transparent z-10 pointer-events-none"></div>

      <div class="absolute inset-0 z-0">
        <img src="./assets/layered_peeks.svg" alt="Layered peaks background"
          class="w-full h-full object-cover opacity-15 mix-blend-multiply" />
      </div>
      <div class="absolute -bottom-32 -right-32 w-96 h-96 bg-blue-100 rounded-full filter blur-3xl opacity-20 z-0"></div>

      <div class="relative z-10">
        <h2 class="text-3xl font-bold text-center mb-12">Key Benefits of Your New eShop</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 max-w-5xl mx-auto">
          <div class="feature-card flex flex-col items-center text-center p-6 bg-white rounded-2xl shadow-lg">
            <BoltIcon class="w-12 h-12 text-blue-600 mb-4" />
            <h3 class="text-xl font-semibold mb-2">Blazing Speed</h3>
            <p class="text-gray-600">Pages load in under 1 second, reducing bounce rates and maximizing sales.</p>
          </div>
          <div class="feature-card flex flex-col items-center text-center p-6 bg-white rounded-2xl shadow-lg">
            <CubeIcon class="w-12 h-12 text-blue-600 mb-4" />
            <h3 class="text-xl font-semibold mb-2">Fully Responsive</h3>
            <p class="text-gray-600">Perfect on desktop, tablet, or mobile—shop from anywhere.</p>
          </div>
          <div class="feature-card flex flex-col items-center text-center p-6 bg-white rounded-2xl shadow-lg">
            <ChartBarIcon class="w-12 h-12 text-blue-600 mb-4" />
            <h3 class="text-xl font-semibold mb-2">Scalable & SEO-Ready</h3>
            <p class="text-gray-600">Grow with confidence—SEO-optimized and built to scale.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Owner-Focused Section -->
    
    <section class="relative py-16 px-8 md:px-16 flex flex-col lg:flex-row items-center gap-12">
        <div class="absolute top-0 left-0 w-full h-24 bg-gradient-to-b from-blue-100 to-transparent z-10 pointer-events-none"></div>
        <div class="lg:w-1/2 flex justify-center owner-image">
            <img src="./assets/owner_interface.jpeg" alt="Admin interface preview"
            class="w-full max-w-lg rounded-3xl shadow-2xl object-cover transition-transform duration-500 hover:scale-105">
        </div>

        <div class="lg:w-1/2 owner-text">
            <h2 class="text-3xl md:text-4xl font-bold leading-snug mb-6">
            Empower Your eShop<br>
            and Focus on What Matters
            </h2>
            <div class="space-y-4 mb-6">
            <div class="flex items-start gap-4">
                <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
                <p class="text-gray-700 leading-relaxed">Manage stock in real-time with an intuitive dashboard</p>
            </div>
            <div class="flex items-start gap-4">
                <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
                <p class="text-gray-700 leading-relaxed">Track and fulfill orders effortlessly</p>
            </div>
            <div class="flex items-start gap-4">
                <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
                <p class="text-gray-700 leading-relaxed">Customize promotions and discounts on the fly</p>
            </div>
            <div class="flex items-start gap-4">
                <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
                <p class="text-gray-700 leading-relaxed">Analyze sales data and customer behavior</p>
            </div>
            </div>
            <p class="text-gray-600">
            Experience the power of a real e-commerce platform. Retain customers, convert traffic, and manage like a pro.
            </p>
        </div>
        </section>


    <!-- Client-Focused Section -->
    <section class="py-16 px-8 md:px-16 flex flex-col lg:flex-row-reverse items-center gap-12">
        <div class="lg:w-1/2 flex justify-center client-image">
            <div class="lg:w-1/2 flex justify-center client-image">
            <img
                src="./assets/client2.png"
                alt="Client interface preview"
                class="w-[80%] max-w-[220px] sm:max-w-xs md:max-w-sm lg:max-w-xs rounded-3xl shadow-2xl object-cover transition-transform duration-500 hover:scale-105"
            />
            </div>
        </div>

        <div class="lg:w-1/2 client-text">
            <h2 class="text-3xl md:text-4xl font-bold leading-snug mb-6">
            A Better Shopping Experience<br>
            Built for Your Customers
            </h2>
            <div class="space-y-4 mb-6">
            <div class="flex items-start gap-4">
                <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
                <p class="text-gray-700 leading-relaxed">Fast page loads and smooth navigation</p>
            </div>
            <div class="flex items-start gap-4">
                <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
                <p class="text-gray-700 leading-relaxed">Mobile-first design for shopping on the go</p>
            </div>
            <div class="flex items-start gap-4">
                <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
                <p class="text-gray-700 leading-relaxed">Secure and simple checkout process</p>
            </div>
            <div class="flex items-start gap-4">
                <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
                <p class="text-gray-700 leading-relaxed">Personalized promotions and offers</p>
            </div>
            </div>
            <p class="text-gray-600">
            Give your customers a polished, trustworthy experience that keeps them coming back—just like their favorite apps.
            </p>
        </div>
    </section>
        <!-- FAQ Section -->
    <section class="faq-section relative py-20 px-8 md:px-16 bg-gray-50 overflow-hidden">
            <!-- Background Wave -->
            <div class="absolute inset-0 z-0 opacity-10">
                <img src="./assets/waves.svg" alt="Wave background" class="w-full h-full object-cover" />
            </div>

            <!-- Blurred blob (optional, subtle effect) -->
            <div class="absolute -top-20 -left-20 w-96 h-96 bg-blue-100 rounded-full mix-blend-multiply filter blur-3xl opacity-20 z-0"></div>

            <!-- FAQ content -->
            <div class="relative z-10">
                <h2 class="text-3xl font-bold text-center mb-10">Frequently Asked Questions</h2>
                <div class="max-w-3xl mx-auto space-y-4">
                <div
                    v-for="(faq, index) in faqs"
                    :key="index"
                    class="border border-gray-200 rounded-xl overflow-hidden bg-white shadow-sm"
                >
                    <button
                    @click="toggleFAQ(index)"
                    class="w-full flex justify-between items-center px-6 py-4 text-left text-lg font-medium hover:bg-gray-100 transition"
                    >
                    {{ faq.question }}
                    <svg
                        :class="{'transform rotate-180': faq.open}"
                        class="w-5 h-5 transition-transform duration-200"
                        fill="none"
                        stroke="currentColor"
                        viewBox="0 0 24 24"
                    >
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
                    </svg>
                    </button>

                    <div v-if="faq.open" class="px-6 pb-4 text-gray-600">
                    {{ faq.answer }}
                    </div>
                </div>
            </div>
        </div>
    </section>
        <!-- CTA Section -->
   
    <section class="relative bg-gradient-to-b from-white to-gray-100 py-20 px-8 text-center cta-section">
    <!-- Top Blue Fade -->
    <div class="absolute top-0 left-0 w-full h-24 bg-gradient-to-b from-blue-100 to-transparent opacity-70 z-10 pointer-events-none"></div>

    <!-- Wrap content with z-20 to appear above the fade -->
    <div class="relative z-20 max-w-2xl mx-auto space-y-6">
        <p class="text-blue-600 font-semibold uppercase">Let’s Talk</p>
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900">
        Ready to launch your high-performing eShop?
        </h2>

        <Transition
        @before-enter="beforeEnter"
        @enter="enter"
        @leave="leave"
        >
        <div v-if="showContact" class="grid grid-cols-1 sm:grid-cols-2 gap-4 mt-8 max-w-xl mx-auto">
            <!-- Phone -->
            <a
            href="tel:+213699999999"
            class="flex items-center gap-4 p-4 bg-white rounded-2xl shadow hover:shadow-lg transition hover:scale-[1.02]"
            >
            <div class="bg-blue-100 text-blue-600 p-2 rounded-full">
                <PhoneIcon class="w-5 h-5" />
            </div>
            <div class="text-left">
                <p class="text-sm text-gray-500">Call Us</p>
                <p class="font-semibold text-gray-800">+213 699 99 99 99</p>
            </div>
            </a>

            <!-- Instagram -->
            <a
            href="https://www.instagram.com/opti.vance"
            target="_blank"
            class="flex items-center gap-4 p-4 bg-white rounded-2xl shadow hover:shadow-lg transition hover:scale-[1.02]"
            >
            <div class="bg-blue-100 text-blue-600 p-2 rounded-full">
                <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                <path
                    d="M7 2C4.243 2 2 4.243 2 7v10c0 2.757 2.243 5 5 5h10c2.757 0 5-2.243 5-5V7c0-2.757-2.243-5-5-5H7zm0 2h10c1.654 0 3 1.346 3 3v10c0 1.654-1.346 3-3 3H7c-1.654 0-3-1.346-3-3V7c0-1.654 1.346-3 3-3zm5 3a5 5 0 100 10 5 5 0 000-10zm0 2a3 3 0 110 6 3 3 0 010-6zm4.5-.5a1.5 1.5 0 11-3.001-.001A1.5 1.5 0 0116.5 6.5z"
                />
                </svg>
            </div>
            <div class="text-left">
                <p class="text-sm text-gray-500">Instagram</p>
                <p class="font-semibold text-gray-800">@Opti.vance</p>
            </div>
            </a>
        </div>
        </Transition>
    </div>
    </section>
    <!-- Footer -->
    <footer class="bg-white border-t border-gray-200 text-center text-sm text-gray-500 py-6">
    <p>&copy; {{ new Date().getFullYear() }} YourBrand. All rights reserved.</p>
    </footer>
  </main>
  
</template>

<style scoped>
.scroll-down-icon {
  animation: bounce 2s infinite;
}
.faq-content {
  overflow: hidden;
}
@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-8px);
  }
}
</style>
