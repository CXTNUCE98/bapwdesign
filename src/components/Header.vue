<script lang="ts" setup>
const menuItems = [
    { label: 'Trang chủ', path: '/' },
    { label: 'Về chúng tôi', path: '/about' },
    { label: 'Dịch vụ', path: '/service' },
    { label: 'Bộ sưu tập', path: '/collections' }
];

const isMenuOpen = ref(false);
const isScrolled = ref(false);

function toggleMenu() {
    isMenuOpen.value = !isMenuOpen.value;
    document.body.classList.toggle('no-scroll', isMenuOpen.value);
}

const closeMenu = () => {
    isMenuOpen.value = false;
    document.body.classList.remove('no-scroll');
};

const handleScroll = () => {
    isScrolled.value = window.scrollY > 20;
};

onMounted(() => {
    window.addEventListener('scroll', handleScroll);
});

onBeforeUnmount(() => {
    window.removeEventListener('scroll', handleScroll);
    document.body.classList.remove('no-scroll');
});

const router = useRouter();
const activeMenu = computed(() => router.currentRoute.value.path);
</script>

<template>
    <header class="fixed top-0 left-0 right-0 z-50 transition-all duration-300 bg-white/90" :class="{
        'bg-white/90 backdrop-blur-sm shadow-sm': isScrolled,
        'bg-transparent': !isScrolled
    }">
        <div class="container mx-auto px-4">
            <nav class="flex items-center justify-between h-20">
                <!-- Logo -->
                <NuxtLink to="/"
                    class="text-40px font-bold flex gap-2 items-end playfair-display text-#292F36 transform transition-all duration-300 hover:scale-105">
                    <img src="../public/logo.png" class="pb-3 h-48px" />
                    Design
                </NuxtLink>

                <!-- Desktop Menu -->
                <ul class="hidden md:flex items-center space-x-8">
                    <li v-for="(item) in menuItems" :key="item.path">
                        <NuxtLink :to="item.path" :class="{ '!text-#CDA274': activeMenu === item.path }"
                            class="text-gray-600 text-20px hover:text-black transition-all duration-300 relative group">
                            {{ item.label }}
                            <span
                                class="absolute bottom-0 left-0 w-0 h-0.5 bg-black transition-all duration-300 group-hover:w-full"></span>
                        </NuxtLink>
                    </li>
                </ul>

                <!-- Mobile Menu Button -->
                <button @click="toggleMenu"
                    class="md:hidden p-2 rounded-full hover:bg-gray-100 transition-colors duration-300">
                    <span class="sr-only">Menu</span>
                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M4 6h16M4 12h16M4 18h16" />
                        <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M6 18L18 6M6 6l12 12" />
                    </svg>
                </button>
            </nav>

            <!-- Mobile Menu -->
            <transition name="slide-right">
                <div v-if="isMenuOpen" class="fixed inset-0 z-50 flex md:hidden">
                    <!-- Overlay -->
                    <div class="flex-1 bg-black/40" @click="closeMenu"></div>

                    <!-- Sidebar -->
                    <div class="w-4/5 max-w-xs bg-white h-full p-6 relative shadow-lg">
                        <!-- Close Button -->
                        <button @click="closeMenu"
                            class="absolute top-4 right-4 text-2xl text-gray-600 hover:text-black">
                            &times;
                        </button>

                        <!-- Menu Items -->
                        <ul class="mt-12 space-y-6">
                            <li v-for="item in menuItems" :key="item.path">
                                <NuxtLink :to="item.path" @click="closeMenu"
                                    :class="{ '!text-[#CDA274]': activeMenu === item.path }"
                                    class="block text-[18px] text-gray-800 playfair-inter hover:text-black transition duration-300">
                                    {{ item.label }}
                                </NuxtLink>
                            </li>
                        </ul>
                    </div>
                </div>
            </transition>
        </div>
    </header>
</template>

<style scoped>
.container {
    max-width: 1200px;
}

.playfair-display {
    font-family: 'Playfair Display', serif;
    font-optical-sizing: auto;
    font-weight: 500;
    font-style: normal;
}

.playfair-inter {
    font-family: 'Playfair Display', serif;
    font-optical-sizing: auto;
    font-weight: 400;
    font-style: normal;
}

/* Slide from right */
.slide-right-enter-active,
.slide-right-leave-active {
    transition: all 0.3s ease;
}

.slide-right-enter-from {
    transform: translateX(100%);
    opacity: 0;
}

.slide-right-enter-to {
    transform: translateX(0);
    opacity: 1;
}

.slide-right-leave-from {
    transform: translateX(0);
    opacity: 1;
}

.slide-right-leave-to {
    transform: translateX(100%);
    opacity: 0;
}

/* Disable scroll */
.no-scroll {
    overflow: hidden;
}

/* Responsive */
@media (max-width: 640px) {
    .container {
        padding-left: 1rem;
        padding-right: 1rem;
    }
}

@media (min-width: 641px) and (max-width: 1024px) {
    .container {
        padding-left: 2rem;
        padding-right: 2rem;
    }
}

@media (min-width: 1025px) {
    .container {
        padding-left: 3rem;
        padding-right: 3rem;
    }
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {

    .slide-right-enter-active,
    .slide-right-leave-active {
        transition: none;
    }
}
</style>
