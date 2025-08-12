<script setup>
import { onMounted } from 'vue'
import {
  ChartBarIcon,
  BoltIcon,
  CubeIcon,
  CheckCircleIcon,
  WrenchScrewdriverIcon,
  PencilSquareIcon,
  ShoppingBagIcon,
  CursorArrowRaysIcon,
  BoldIcon,
  PencilIcon
} from '@heroicons/vue/24/outline' // use outline for a clean bordered look
import { ArrowDownIcon } from '@heroicons/vue/24/solid'
import { PhoneIcon, DevicePhoneMobileIcon } from '@heroicons/vue/24/solid'
import gsap from 'gsap'
import ScrollTrigger from 'gsap/ScrollTrigger'
import { computed, Transition } from 'vue'
import { watch } from 'vue'
import { ref } from 'vue'
const language = ref('en')
const currentLang = computed(() => translations[language.value] || translations.en)
const translations = {
  en: {
    brand: 'Optivance',
    heroTitlePart1: 'Build a Real',
    heroTitleHighlight: 'Online Presence',
    heroSubtitle: 'That Turns Clicks Into Customers',
    heroDescription: 'Get a tailor-made eShop website delivered in record time, optimized for speed and designed to convert your Instagram followers into loyal customers.',
    seeFeatures: 'See Features',
    featuresTitle: 'Key Benefits of Your New eShop',
    
    feature1: 'Blazing Speed',
    feature1desc: 'Pages load in under 1 second, reducing bounce rates and maximizing sales.',
    feature2: 'Easy to Update',
    feature2desc: 'No tech skills needed — update your products and content anytime in just a few clicks.',
    feature3: 'Shopper-Friendly Design',
    feature3desc: 'From smooth scrolling to clear product displays, your shop gives customers an easy, enjoyable way to browse and place orders.',

    // ✅ Owner-Focused Section
    ownerTitle1: 'Empower Your eShop',
    ownerTitle2: 'and Focus on What Matters',
    ownerBullets: [
      'Manage stock in real-time with an intuitive dashboard',
      'Track and fulfill orders effortlessly',
      'Customize promotions and discounts on the fly',
      'Analyze sales data and customer behavior'
    ],
    ownerDesc: 'Experience the power of a real e-commerce platform. Retain customers, convert traffic, and manage like a pro.',

    // ✅ Client-Focused Section
    clientTitle1: 'A Better Shopping Experience',
    clientTitle2: 'Built for Your Customers',
    clientBullets: [
      'Fast page loads and smooth navigation',
      'Mobile-first design for shopping on the go',
      'Simple and intuitive ordering process',
      'Easy access to complete product details'
    ],
    clientDesc: 'Give your customers a polished, trustworthy experience that keeps them coming back—just like their favorite apps.',

    // ✅ FAQ Section
    faqTitle: 'Frequently Asked Questions',
    faqs: [
      {
        question: 'Will I be able to manage the site myself?',
        answer: 'Yes, the admin dashboard is simple and built for non-technical users to update products, track orders, and run promotions.',
        open: false
      },
      {
        question: 'How long does it take to get my eShop live?',
        answer: 'Most websites are delivered in under 5 days, ready to accept orders immediately.',
        open: false
      },
      {
        question: 'Can I connect my delivery service like Yalidine or others?',
        answer: 'Yes — orders can be forwarded to your delivery provider like Yalidine, Zr express, or others.',
        open: false
      },
      {
        question: 'What does it cost to get my eShop?',
        answer: 'Prices vary depending on features, but we keep things affordable and transparent. Message us and we’ll give you a fast, no-pressure quote.',
        open: false
      }
    ],

    // ✅ CTA Section
    ctaLabel: 'Let’s Talk',
    ctaTitle: 'Ready to launch your high-performing eShop?'
  },
  fr: {
    brand: 'Optivance',
    heroTitlePart1: 'Créez une vraie',
    heroTitleHighlight: 'présence en ligne',
    heroSubtitle: 'Qui transforme les clics en clients',
    heroDescription: 'Obtenez une boutique en ligne sur mesure livrée en un temps record, optimisée pour la vitesse et conçue pour convertir vos abonnés Instagram en clients fidèles.',
    seeFeatures: 'Voir les fonctionnalités',
    featuresTitle: 'Avantages clés de votre nouvelle boutique',
    feature1: 'Vitesse fulgurante',
    feature1desc: 'Les pages se chargent en moins d’une seconde, réduisant les taux de rebond et maximisant les ventes.',
    feature2: 'Facile à mettre à jour',
    feature2desc: 'Pas besoin de compétences techniques — mettez à jour vos produits et contenus en quelques clics.',
    feature3: 'Design convivial pour les acheteurs',
    feature3desc: 'Défilement fluide et affichage clair des produits, vos clients profitent d’une navigation agréable.',

    // ✅ Owner-Focused Section
    ownerTitle1: 'Optimisez votre boutique',
    ownerTitle2: 'et concentrez-vous sur l’essentiel',
    ownerBullets: [
      'Gérez les stocks en temps réel avec un tableau de bord intuitif',
      'Suivez et traitez les commandes facilement',
      'Créez des promotions et remises en quelques clics',
      'Analysez les ventes et le comportement client'
    ],
    ownerDesc: 'Profitez d’une vraie plateforme e-commerce. Fidélisez, convertissez, gérez en toute simplicité.',

    // ✅ Client-Focused Section
    clientTitle1: 'Une meilleure expérience d’achat',
    clientTitle2: 'Pensée pour vos clients',
    clientBullets: [
      'Chargement rapide et navigation fluide',
      'Design mobile-first pour les achats en déplacement',
      'Commande simple et intuitive',
      'Accès facile à toutes les informations produit'
    ],
    clientDesc: 'Offrez une expérience digne d’une application moderne : claire, fiable et agréable à utiliser.',

    // ✅ FAQ Section
    faqTitle: 'Questions fréquentes',
    faqs: [
      {
        question: 'Pourrai-je gérer le site moi-même ?',
        answer: 'Oui, le tableau de bord est simple et conçu pour les utilisateurs non techniques afin de mettre à jour les produits, suivre les commandes et gérer les promotions.',
        open: false
      },
      {
        question: 'Combien de temps faut-il pour mettre en ligne ma boutique ?',
        answer: 'La plupart des sites sont livrés en moins de 5 jours, prêts à accepter des commandes immédiatement.',
        open: false
      },
      {
        question: 'Puis-je connecter mon service de livraison comme Yalidine ?',
        answer: 'Oui — les commandes peuvent être transférées à votre prestataire de livraison comme Yalidine, Zr express ou autres.',
        open: false
      },
      {
        question: 'Combien coûte la création de ma boutique ?',
        answer: 'Les prix varient selon les fonctionnalités, mais nous restons abordables et transparents. Écrivez-nous pour un devis rapide sans engagement.',
        open: false
      }
    ],

    ctaLabel: 'Discutons-en',
    ctaTitle: 'Prêt à lancer votre boutique performante ?'
  },
  ar: {
    brand: 'أوبتيفانس',
    heroTitlePart1: 'أنشئ',
    heroTitleHighlight: 'حضورًا رقميًا حقيقيًا',
    heroSubtitle: 'يحول النقرات إلى عملاء',
    heroDescription: 'احصل على متجر إلكتروني مصمم خصيصًا يتم تسليمه في وقت قياسي، ومحسن للسرعة ومصمم لتحويل متابعيك على إنستغرام إلى عملاء أوفياء.',
    seeFeatures: 'عرض الميزات',
    featuresTitle: 'الفوائد الرئيسية لمتجرك الجديد',

    feature1: 'سرعة مذهلة',
    feature1desc: 'يتم تحميل الصفحات في أقل من ثانية، مما يقلل من معدلات الارتداد ويزيد من المبيعات.',
    feature2: 'سهل التحديث',
    feature2desc: 'لا تحتاج إلى مهارات تقنية — حدّث منتجاتك ومحتواك ببضع نقرات فقط.',
    feature3: 'تصميم مناسب للمشتري',
    feature3desc: 'من التمرير السلس إلى عرض المنتجات الواضح، يحصل عملاؤك على تجربة تصفح مريحة.',

    // ✅ Owner-Focused Section
    ownerTitle1: 'قم بتحسين متجرك',
    ownerTitle2: 'وركّز على ما يهم',
    ownerBullets: [
      'إدارة المخزون مباشرة من لوحة تحكم سهلة',
      'تتبع ومعالجة الطلبات بكل سهولة',
      'إنشاء عروض وتخفيضات بنقرات بسيطة',
      'تحليل المبيعات وسلوك العملاء'
    ],
    ownerDesc: 'منصة تجارة إلكترونية حقيقية تمنحك التحكم الكامل — سهولة في الإدارة، وفعالية في النتائج.',

    // ✅ Client-Focused Section
    clientTitle1: 'تجربة تسوق أفضل',
    clientTitle2: 'مصممة خصيصًا لعملائك',
    clientBullets: [
      'تحميل سريع وتنقل سلس',
      'تصميم أولويته الهاتف المحمول للشراء أثناء التنقل',
      'إجراء طلب مبسط وسهل',
      'الوصول السريع لجميع معلومات المنتج'
    ],
    clientDesc: 'قدّم تجربة تسوق سلسة وعصرية تجعل عملاءك يعودون إليك مجددًا.',

    // ✅ FAQ Section
    faqTitle: 'الأسئلة الشائعة',
    faqs: [
      {
        question: 'هل سأتمكن من إدارة الموقع بنفسي؟',
        answer: 'نعم، لوحة التحكم بسيطة ومصممة للمستخدمين غير التقنيين لتحديث المنتجات وتتبع الطلبات وتفعيل العروض.',
        open: false
      },
      {
        question: 'كم من الوقت يستغرق إطلاق متجري الإلكتروني؟',
        answer: 'معظم المواقع تُسلّم خلال أقل من 5 أيام، جاهزة لاستقبال الطلبات فورًا.',
        open: false
      },
      {
        question: 'هل يمكنني ربط خدمة توصيل مثل ياليدين؟',
        answer: 'نعم — يمكن تحويل الطلبات إلى مزود التوصيل الخاص بك مثل ياليدين، زد إكسبرس، وغيرهم.',
        open: false
      },
      {
        question: 'كم تكلفة إنشاء المتجر الإلكتروني؟',
        answer: 'التكلفة تعتمد على الميزات، لكننا نحافظ على الشفافية والأسعار المعقولة. راسلنا للحصول على عرض سعر سريع وبدون التزام.',
        open: false
      }
    ],

    ctaLabel: 'تواصل معنا',
    ctaTitle: 'هل أنت مستعد لإطلاق متجرك عالي الأداء؟'
  }

}

const t = computed(() => translations[language.value])

const showContact = ref(true)
const faqs = ref([])

// Watch language and update faqs accordingly
watch(language, () => {
  // Deep clone to avoid mutating the source in translations
  faqs.value = t.value.faqs.map(f => ({ ...f }))
}, { immediate: true })


function toggleFAQ(index) {
  faqs.value[index].open = !faqs.value[index].open
}

gsap.registerPlugin(ScrollTrigger)

function scrollToFeatures() {
  const el = document.getElementById('features')
  el && el.scrollIntoView({ behavior: 'smooth' })
}

import {nextTick} from 'vue'

const faqAnswer = ref(null)

function beforeEnter(el) {
  el.style.height = '0'
  el.style.opacity = '0'
}

function enter(el, done) {
  nextTick(() => {
    const height = el.scrollHeight
    el.style.transition = 'height 0.4s ease, opacity 0.4s ease'
    el.style.height = height + 'px'
    el.style.opacity = '1'
    el.addEventListener('transitionend', (e) => {
      if (e.propertyName === 'height') {
        el.style.height = 'auto'
        done()
      }
    }, { once: true })
  })
}

function leave(el, done) {
  // Set the current height explicitly first
  el.style.height = el.scrollHeight + 'px'
  el.style.transition = 'none' // Remove transition temporarily
  
  // Force a repaint to ensure the height is set
  void el.offsetHeight
  
  // Now add transition and animate to 0
  el.style.transition = 'height 0.4s ease, opacity 0.4s ease'
  
  // Use requestAnimationFrame to ensure the transition applies properly
  requestAnimationFrame(() => {
    el.style.height = '0'
    el.style.opacity = '0'
  })

  el.addEventListener('transitionend', (e) => {
    if (e.propertyName === 'height') {
      done()
    }
  }, { once: true })
}
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
    // ✅ Fixes the first-scroll issue
    ScrollTrigger.refresh()
})
</script>

<template>
  <main class="bg-white text-gray-900 scroll-smooth max-w-screen overflow-x-hidden">
    <!-- Hero -->
    <header class="relative overflow-hidden bg-white">
    <!-- Brand Top Bar -->
    <div class="relative z-20 flex items-center justify-between px-8 md:px-16 py-4">
    <span class="text-xl font-bold text-gray-900 tracking-tight">
      Opti<span class="text-xl font-bold text-blue-600 tracking-tight">vance</span>
    </span>

    <!-- Language Toggle Buttons -->
    <div class="flex gap-4 items-center text-2xl">
      <button
        @click="language = 'en'"
        :class="{ 'opacity-100': language === 'en', 'opacity-50': language !== 'en' }"
        class="transition-opacity flex items-center gap-1"
      >
        <span class="fi fi-gb w-6 h-6"></span>
      </button>
      <button
        @click="language = 'fr'"
        :class="{ 'opacity-100': language === 'fr', 'opacity-50': language !== 'fr' }"
        class="transition-opacity flex items-center gap-1"
      >
        <span class="fi fi-fr w-6 h-6"></span>
      </button>
      <button
        @click="language = 'ar'"
        :class="{ 'opacity-100': language === 'ar', 'opacity-50': language !== 'ar' }"
        class="transition-opacity flex items-center gap-1"
      >
        <span class="fi fi-dz w-6 h-6"></span>
      </button>
    </div>

    </div>

      <div class="absolute inset-0 z-0">
        <img src="./assets/waves.svg" class="w-full h-full object-cover opacity-10" alt="Decorative background" />
      </div>
      <div class="absolute -top-20 -left-20 w-96 h-96 bg-blue-300 rounded-full mix-blend-multiply filter blur-3xl opacity-30 z-0"></div>

      <div class="relative z-10 grid grid-cols-1 md:grid-cols-2 items-center gap-8 p-8 md:p-16">
        <section class="flex justify-center md:justify-end">
          <div class="w-full max-w-md aspect-w-4 aspect-h-3">
            <img
              src="./assets/example-shop.jpeg"
              alt="Example eShop preview"
              loading="lazy"
              class="w-full h-full object-cover rounded-3xl shadow-2xl transition-transform duration-500 hover:scale-105"
            />
          </div>
        </section>

        <section class="flex flex-col gap-6">
          <h1 class="text-4xl md:text-5xl font-extrabold leading-tight">
            <span>{{ t.heroTitlePart1 + " " }} </span>
            <span class="text-blue-600">{{ t.heroTitleHighlight }}</span><br>
            <span class="text-gray-900">{{ t.heroSubtitle }}</span>
          </h1>
          <p class="text-lg text-gray-500 max-w-md">
            {{ t.heroDescription }}
          </p>
          <button @click="scrollToFeatures"
            class="inline-flex items-center gap-2 px-6 py-3 text-white bg-blue-600 hover:bg-blue-700 transition rounded-lg text-lg font-semibold shadow-md">
            {{ t.seeFeatures }}
            <ArrowDownIcon class="w-5 h-5 scroll-down-icon" />
          </button>
        </section>
      </div>
    </header>

    <!-- Features Section -->
    <section id="features" class="relative py-24 px-8 md:px-16 bg-white overflow-hidden">
    <!-- Top Fade Background -->
    <div class="absolute top-0 left-0 w-full h-24 bg-gradient-to-b from-blue-100 to-transparent z-10 pointer-events-none"></div>

      <div class="absolute inset-0 z-0">
        <img src="./assets/layered_peeks.svg" alt="Layered peaks background"
          class="w-full h-full object-cover opacity-15 mix-blend-multiply" />
      </div>
      <div class="absolute -bottom-32 -right-32 w-96 h-96 bg-blue-100 rounded-full filter blur-3xl opacity-20 z-0"></div>

      <div class="relative z-10">
        <h2 class="text-3xl font-bold text-center mb-12">{{ t.featuresTitle }}</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 max-w-5xl mx-auto">
          <div class="feature-card flex flex-col items-center text-center p-6 bg-white rounded-2xl shadow-lg">
            <BoltIcon class="w-12 h-12 text-blue-600 mb-4" />
            <h3 class="text-xl font-semibold mb-2">{{ t.feature1 }}</h3>
            <p class="text-gray-600">{{ t.feature1desc }}</p>
          </div>
          <div class="feature-card flex flex-col items-center text-center p-6 bg-white rounded-2xl shadow-lg">
            <PencilSquareIcon class="w-12 h-12 text-blue-600 mb-4" />
            <h3 class="text-xl font-semibold mb-2">{{ t.feature2 }}</h3>
            <p class="text-gray-600">{{ t.feature2desc }}</p>
          </div>
          <div class="feature-card flex flex-col items-center text-center p-6 bg-white rounded-2xl shadow-lg">
            <ShoppingBagIcon class="w-12 h-12 text-blue-600 mb-4" />
            <h3 class="text-xl font-semibold mb-2">{{ t.feature3 }}</h3>
            <p class="text-gray-600">{{ t.feature3desc }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Owner-Focused Section -->
    <section class="relative py-16 px-8 md:px-16 flex flex-col lg:flex-row items-center gap-12">
      <div class="absolute top-0 left-0 w-full h-24 bg-gradient-to-b from-blue-100 to-transparent z-10 pointer-events-none"></div>

      <div class="lg:w-1/2 flex justify-center owner-image">
        <img
          src="./assets/owner_interface.jpeg"
          alt="Admin interface preview"
          class="w-full max-w-lg rounded-3xl shadow-2xl object-cover transition-transform duration-500 hover:scale-105"
        />
      </div>

      <div class="lg:w-1/2 owner-text">
        <h2 class="text-3xl md:text-4xl font-bold leading-snug mb-6">
          {{ t.ownerTitleLine1 }}<br />
          {{ t.ownerTitleLine2 }}
        </h2>

        <div class="space-y-4 mb-6">
          <div class="flex items-start gap-4">
            <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
            <p class="text-gray-700 leading-relaxed">{{ t.ownerBullets[0] }}</p>
          </div>
          <div class="flex items-start gap-4">
            <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
            <p class="text-gray-700 leading-relaxed">{{ t.ownerBullets[1] }}</p>
          </div>
          <div class="flex items-start gap-4">
            <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
            <p class="text-gray-700 leading-relaxed">{{ t.ownerBullets[2] }}</p>
          </div>
          <div class="flex items-start gap-4">
            <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
            <p class="text-gray-700 leading-relaxed">{{ t.ownerBullets[3] }}</p>
          </div>
        </div>

        <p class="text-gray-600">{{ t.ownerDescription }}</p>
      </div>
    </section>

    <!-- Client-Focused Section -->
    <section class="py-16 px-8 md:px-16 flex flex-col lg:flex-row-reverse items-center gap-12">
      <div class="lg:w-1/2 flex justify-center client-image">
        <img
          src="./assets/client2.png"
          alt="Client interface preview"
          class="w-[80%] max-w-[220px] sm:max-w-xs md:max-w-sm lg:max-w-xs rounded-3xl shadow-2xl object-cover transition-transform duration-500 hover:scale-105"
        />
      </div>

      <div class="lg:w-1/2 client-text">
        <h2 class="text-3xl md:text-4xl font-bold leading-snug mb-6">
          {{ t.clientTitleLine1 }}<br />
          {{ t.clientTitleLine2 }}
        </h2>

        <div class="space-y-4 mb-6">
          <div class="flex items-start gap-4">
            <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
            <p class="text-gray-700 leading-relaxed">{{ t.clientBullets[0] }}</p>
          </div>
          <div class="flex items-start gap-4">
            <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
            <p class="text-gray-700 leading-relaxed">{{ t.clientBullets[1] }}</p>
          </div>
          <div class="flex items-start gap-4">
            <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
            <p class="text-gray-700 leading-relaxed">{{ t.clientBullets[2] }}</p>
          </div>
          <div class="flex items-start gap-4">
            <CheckCircleIcon class="w-6 h-6 text-blue-600 shrink-0" />
            <p class="text-gray-700 leading-relaxed">{{ t.clientBullets[3] }}</p>
          </div>
        </div>

        <p class="text-gray-600">{{ t.clientDescription }}</p>
      </div>
    </section>

        <!-- FAQ Section -->
    <section 
      class="faq-section relative py-20 px-8 md:px-16 bg-gray-50 overflow-hidden"
      :class="{ 'rtl': language === 'ar' }"
    >
      <!-- Background Wave -->
      <div class="absolute inset-0 z-0 opacity-10">
        <img src="./assets/waves.svg" alt="Wave background" class="w-full h-full object-cover" />
      </div>

      <!-- Blurred blob -->
      <div class="absolute -top-20 -left-20 w-96 h-96 bg-blue-100 rounded-full mix-blend-multiply filter blur-3xl opacity-20 z-0"></div>

      <!-- FAQ Content -->
      <div class="relative z-10">
        <h2 class="text-3xl font-bold text-center mb-10">{{ t.faqTitle }}</h2>

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
                :class="{ 'transform rotate-180': faq.open }"
                class="w-5 h-5 transition-transform duration-200"
                fill="none"
                stroke="currentColor"
                viewBox="0 0 24 24"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
              </svg>
            </button>

            <Transition
              @before-enter="beforeEnter"
              @enter="enter"
              @leave="leave"
            >
              <div v-if="faq.open" ref="faqAnswer" class="px-6 text-gray-600 overflow-hidden">
                {{ faq.answer }}
              </div>
            </Transition>
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
        <p class="text-blue-600 font-semibold uppercase">{{ t.ctaLabel }}</p>
        <h2 class="text-3xl md:text-4xl font-bold text-gray-900">
        {{ t.ctaTitle }}
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
                <p class="font-semibold text-gray-800">+213 675 98 69 88</p>
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
    <p>&copy; {{ new Date().getFullYear() }} {{ t.brand }} Dz. All rights reserved.</p>
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
