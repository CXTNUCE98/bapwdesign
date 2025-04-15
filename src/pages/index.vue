<script lang="ts" setup>
import { ref, onMounted } from 'vue';

// Dữ liệu stats
const stats = [
    { id: 1, number: 12, displayNumber: ref(0), label: 'Kinh nghiệm' },
    { id: 2, number: 85, displayNumber: ref(0), label: 'Sản phẩm' },
    { id: 3, number: 15, displayNumber: ref(0), label: 'Đã xuất bản' },
    { id: 4, number: 10, displayNumber: ref(0), label: 'Người khách hàng' }
];

const testimonials = [
    {
        name: 'Đặng Tuyết Anh',
        role: 'Thanh Xuân, Hà Nội',
        comment: '"Tôi chọn B Design vì sự chỉn chu trong từng chi tiết. Khi nhận được sản phẩm, tôi biết mình đã chọn đúng nơi"'
    },
    {
        name: 'Đặng Tuyết Anh',
        role: 'Thanh Xuân, Hà Nội',
        comment: '"Tôi chọn B Design vì sự chỉn chu trong từng chi tiết. Khi nhận được sản phẩm, tôi biết mình đã chọn đúng nơi"'
    },
    {
        name: 'Đặng Tuyết Anh',
        role: 'Thanh Xuân, Hà Nội',
        comment: '"Tôi chọn B Design vì sự chỉn chu trong từng chi tiết. Khi nhận được sản phẩm, tôi biết mình đã chọn đúng nơi"'
    }
];

const statsRef = ref(null);
const hasAnimated = ref(false);

onMounted(() => {
    // Tạo intersection observer để theo dõi khi phần tử xuất hiện trong viewport
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting && !hasAnimated.value) {
                animateNumbers();
                hasAnimated.value = true;
            }
        });
    }, { threshold: 0.1 });

    // Gắn observer vào phần tử stats
    if (statsRef.value) {
        observer.observe(statsRef.value);
    }
});

function animateNumbers() {
    stats.forEach((stat, index) => {
        // Thêm độ trễ cho mỗi số
        setTimeout(() => {
            const duration = 2000; // Thời gian animation (ms)
            const finalNumber = stat.number;
            const startTime = performance.now();

            function updateNumber(timestamp) {
                const elapsed = timestamp - startTime;
                const progress = Math.min(elapsed / duration, 1);

                // Hàm easing đơn giản
                const easing = 1 - Math.pow(1 - progress, 3);
                stat.displayNumber.value = Math.round(easing * finalNumber);

                if (progress < 1) {
                    requestAnimationFrame(updateNumber);
                } else {
                    stat.displayNumber.value = finalNumber;
                }
            }

            requestAnimationFrame(updateNumber);
        }, index * 150); // Khởi động mỗi số sau 150ms
    });
}
</script>

<template>
    <main class="min-h-screen bg-white">
        <!-- Hero Section -->
        <HeroSection />
        <!-- Collections Grid -->
        <CollectionGrid />
        <!-- About Section -->
        <AboutSection />

        <!-- Stats Section -->
        <section ref="statsRef" class="bg-[#F4F0EC] h-[1048px] md:h-[480px] flex justify-center items-center mt-20">
            <div class="container mx-auto px-4">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                    <div v-for="(stat, index) in stats" :key="stat.id"
                        class="text-center transform transition-all duration-700 h-[155px] flex flex-col justify-center"
                        :class="{ 'md:border-l md:border-[#CDA274]': index !== 0 }"
                        :style="{ transitionDelay: index * 100 + 'ms' }">
                        <h3 class="text-[85px] font-bold text-[#C4A484] mb-2 dm-serif odometer-animation">
                            {{ stat.displayNumber }}
                        </h3>
                        <p class="text-gray-600 text-[22px]">{{ stat.label }}</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Collections -->
        <Collections />

        <!-- Testimonials Section -->
        <section class="py-20 md:px-0 px-4">
            <div class="container mx-auto rounded-[48px] bg-[#F4F0EC] px-4 md:px-8 py-12">
                <h2 class="text-[32px] md:text-[50px] text-center mb-12 font-500 playfair-display text-[#292F36]">Khách
                    hàng nghĩ gì về chúng tôi</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                    <div v-for="(testimonial, index) in testimonials" :key="index"
                        class="bg-white p-6 rounded-[32px] shadow-lg transform transition-all duration-700"
                        :style="{ transitionDelay: index * 100 + 'ms' }">
                        <div class="flex items-center gap-4 mb-4">
                            <img src="https://static.vecteezy.com/system/resources/previews/025/402/511/large_2x/statue-of-model-mannequin-in-showcasing-fashion-formal-clothes-in-abstract-concept-isolate-on-multi-color-pastel-background-promotion-discount-sale-with-geometric-shape-product-stand-3d-rendering-photo.jpg"
                                alt="Avatar" class="w-12 h-12 rounded-full">
                            <div class="font-400">
                                <h4 class="font-semibold playfair-display text-[25px]">{{ testimonial.name }}</h4>
                                <p class="text-[16px] text-gray-600">{{ testimonial.role }}</p>
                            </div>
                        </div>
                        <p class="text-gray-600 italic text-[18px] font-300">{{ testimonial.comment }}</p>
                    </div>
                </div>
            </div>
        </section>
    </main>
</template>

<style scoped>
.honey-img {
    height: 690px;
    width: 474px;
    overflow: hidden;
}

.vertical-text {
    writing-mode: vertical-rl;
    text-orientation: mixed;
    transform: rotate(180deg);
    white-space: nowrap;
    font-family: Arial, sans-serif;
    font-size: 51px;
    color: #E6E6E6;
    font-weight: bold;
}

/* Hiệu ứng đếm số */
.odometer-animation {
    display: inline-block;
    position: relative;
}

.odometer-animation span {
    font-size: 16px;
    vertical-align: super;
    opacity: 0.8;
}

/* CSS cơ bản */
.container {
    max-width: 1136px;
}

/* Smooth transitions */
.transition-all {
    transition-property: all;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

/* Media queries */
@media (max-width: 768px) {
    .odometer-animation {
        font-size: 65px;
    }
}

.dm-serif {
    font-family: "DM Serif Display", serif;
    font-weight: 400;
    font-style: normal;
}

.playfair-display {
    font-family: "Playfair Display", serif;
    font-optical-sizing: auto;
    font-style: normal;
}
</style>