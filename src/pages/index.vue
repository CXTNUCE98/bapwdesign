<script lang="ts" setup>


const collections = [
    {
        title: 'Collection',
        description: 'Here are many variations of the passages of the available, majority',
        image: 'https://static.vecteezy.com/system/resources/previews/025/402/511/large_2x/statue-of-model-mannequin-in-showcasing-fashion-formal-clothes-in-abstract-concept-isolate-on-multi-color-pastel-background-promotion-discount-sale-with-geometric-shape-product-stand-3d-rendering-photo.jpg'
    },
    {
        title: 'Collection',
        description: 'Here are many variations of the passages of the available, majority',
        image: 'https://static.vecteezy.com/system/resources/previews/025/402/511/large_2x/statue-of-model-mannequin-in-showcasing-fashion-formal-clothes-in-abstract-concept-isolate-on-multi-color-pastel-background-promotion-discount-sale-with-geometric-shape-product-stand-3d-rendering-photo.jpg'
    },
    {
        title: 'Collection',
        description: 'Here are many variations of the passages of the available, majority',
        image: 'https://static.vecteezy.com/system/resources/previews/025/402/511/large_2x/statue-of-model-mannequin-in-showcasing-fashion-formal-clothes-in-abstract-concept-isolate-on-multi-color-pastel-background-promotion-discount-sale-with-geometric-shape-product-stand-3d-rendering-photo.jpg'
    }
];

const stats = [
    { number: '12', label: 'Kinh nghiệm' },
    { number: '85', label: 'Sản phẩm' },
    { number: '15', label: 'Đã xuất bản' },
    { number: '10', label: 'Người khách hàng' }
];


const testimonials = [
    {
        name: 'Đặng Tuyết Anh',
        role: 'Thanh Xuân, Hà Nội',
        comment: '“Tôi chọn B Design vì sự chỉn chu trong từng chi tiết. Khi nhận được sản phẩm, tôi biết mình đã chọn đúng nơi”'
    },
    {
        name: 'Đặng Tuyết Anh',
        role: 'Thanh Xuân, Hà Nội',
        comment: '“Tôi chọn B Design vì sự chỉn chu trong từng chi tiết. Khi nhận được sản phẩm, tôi biết mình đã chọn đúng nơi”'
    },
    {
        name: 'Đặng Tuyết Anh',
        role: 'Thanh Xuân, Hà Nội',
        comment: '“Tôi chọn B Design vì sự chỉn chu trong từng chi tiết. Khi nhận được sản phẩm, tôi biết mình đã chọn đúng nơi”'
    }
];
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
        <section class="bg-#F4F0EC h-1048px md:h-480px flex justify-center items-center mt-20">
            <div class="container mx-auto px-4  ">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-8 ">
                    <div v-for="(stat, index) in stats" :key="index"
                        class="text-center transform transition-all duration-700 h-155px flex flex-col justify-center "
                        :class="{ 'md:(border-l-1 border-#CDA274)': index !== 0 }"
                        :style="{ transitionDelay: index * 100 + 'ms' }">
                        <h3 class="text-85px font-bold text-[#C4A484] mb-2 dm-serif">{{ stat.number }}</h3>
                        <p class="text-gray-600 text-22px">{{ stat.label }}</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Collections -->
        <Collections />

        <!-- Testimonials Section -->
        <section class="py-20 ">
            <div class="container mx-auto rounded-48px bg-#F4F0EC px-8 py-12">
                <h2 class="text-50px text-center mb-12 font-600 playfair-display text-#292F36">Khách hàng nghĩ gì về chúng tôi</h2>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-8 ">

                    <div v-for="(testimonial, index) in testimonials" :key="index"
                        class="bg-white p-6 rounded-32px shadow-lg transform transition-all duration-700 "
                        :style="{ transitionDelay: index * 100 + 'ms' }">
                        <div class="flex items-center gap-4 mb-4">
                            <img src="https://static.vecteezy.com/system/resources/previews/025/402/511/large_2x/statue-of-model-mannequin-in-showcasing-fashion-formal-clothes-in-abstract-concept-isolate-on-multi-color-pastel-background-promotion-discount-sale-with-geometric-shape-product-stand-3d-rendering-photo.jpg"
                                alt="Avatar" class="w-12 h-12 rounded-full">
                            <div class="playfair-display font-400">
                                <h4 class="font-semibold text-25px">{{ testimonial.name }}</h4>
                                <p class="text-18px text-gray-600">{{ testimonial.role }}</p>
                            </div>
                        </div>
                        <p class="text-gray-600 italic text-18px font-300">{{ testimonial.comment }}</p>
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

/* Add any custom styles here */
.container {
    max-width: 1136px;
}

/* Smooth transitions */
.transition-all {
    transition-property: all;
    transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

/* Transform utilities */

/* Media queries */
@media (max-width: 768px) {
    .grid-cols-1 {
        grid-template-columns: repeat(1, minmax(0, 1fr));
    }

    .grid-cols-2 {
        grid-template-columns: repeat(2, minmax(0, 1fr));
    }
}

@media (min-width: 769px) {
    .md\:grid-cols-3 {
        grid-template-columns: repeat(3, minmax(0, 1fr));
    }

    .md\:grid-cols-4 {
        grid-template-columns: repeat(4, minmax(0, 1fr));
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