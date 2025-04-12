<script setup lang="ts">
import emblaCarouselVue from 'embla-carousel-vue'
import Autoplay from 'embla-carousel-autoplay'

import BgAboutUs from "@/public/bg-about-us.png"
import DoubleQuotes from "@/public/double-quotes.png"

const [emblaRef, emblaApi] = emblaCarouselVue({ loop: true, align: 'start' }, [Autoplay({delay: 40000})])

const scrollPrev = () => {
    if (emblaApi.value) emblaApi.value.scrollPrev()
}

const scrollNext = () => {
    if (emblaApi.value) emblaApi.value.scrollNext()
}

const commentList = [
    {
        avatar: 'https://dybedu.com.vn/wp-content/uploads/hinh-nen-luffy-gear-5.jpg',
        comment: 'Vel officiis dolor ea illo aut eligendi ullam non laudantium magnam et recusandae molestiae sit iure unde aut voluptate quaerat. Id sunt provident quo possimus impedit vel doloremque obcaecati qui ullam consectetur et ipsum omnis.',
        name: 'John Doe',
        job: 'Painter',
    },
    {
        avatar: 'https://vcdn1-ngoisao.vnecdn.net/2024/04/14/kimb-jpeg-6135-1713095753.jpg?w=460&h=0&q=100&dpr=2&fit=crop&s=yAc3wPlMHsg1axzjVTJORA',
        comment: 'Vel officiis dolor ea illo aut eligendi ullam non laudantium magnam et recusandae molestiae sit iure unde aut voluptate quaerat. Id sunt provident quo possimus impedit vel doloremque obcaecati qui ullam consectetur et ipsum omnis.',
        name: 'Kim Soo Hyun',
        job: 'Actor',
    },
    {
        avatar: 'https://upload.wikimedia.org/wikipedia/commons/7/78/Andriy_Shevchenko_2017.jpg',
        comment: 'Vel officiis dolor ea illo aut eligendi ullam non laudantium magnam et recusandae molestiae sit iure unde aut voluptate quaerat. Id sunt provident quo possimus impedit vel doloremque obcaecati qui ullam consectetur et ipsum omnis.',
        name: 'Shevchenko',
        job: 'Football player',
    },
    {
        avatar: 'https://ntvb.tmsimg.com/assets/assets/501949_v9_bb.jpg',
        comment: 'Vel officiis dolor ea illo aut eligendi ullam non laudantium magnam et recusandae molestiae sit iure unde aut voluptate quaerat. Id sunt provident quo possimus impedit vel doloremque obcaecati qui ullam consectetur et ipsum omnis.',
        name: 'Beckham',
        job: 'Football player',
    },
    {
        avatar: 'https://photo.znews.vn/w660/Uploaded/bpivpawv/2024_02_25/Xabi_Alonso.jpeg',
        comment: 'Vel officiis dolor ea illo aut eligendi ullam non laudantium magnam et recusandae molestiae sit iure unde aut voluptate quaerat. Id sunt provident quo possimus impedit vel doloremque obcaecati qui ullam consectetur et ipsum omnis.',
        name: 'Xabi Alonso',
        job: 'Football player',
    },
    {
        avatar: 'https://romapress.net/wp-content/uploads/2023/12/mourinho2-3-700x467.jpg',
        comment: 'Vel officiis dolor ea illo aut eligendi ullam non laudantium magnam et recusandae molestiae sit iure unde aut voluptate quaerat. Id sunt provident quo possimus impedit vel doloremque obcaecati qui ullam consectetur et ipsum omnis.',
        name: 'Jose Mourinho',
        job: 'Coach',
    },
    {
        avatar: 'https://www.vietnam.vn/wp-content/uploads/2024/05/Ly-Hien-la-nan-nhan-trong-phim-Sac-xuan-gui.jpeg',
        comment: 'Vel officiis dolor ea illo aut eligendi ullam non laudantium magnam et recusandae molestiae sit iure unde aut voluptate quaerat. Id sunt provident quo possimus impedit vel doloremque obcaecati qui ullam consectetur et ipsum omnis.',
        name: 'Lý Hiện',
        job: 'Actor',
    }
]
</script>
<template>
    <div class="h-768px relative">
        <img :src="BgAboutUs" alt="bg-about" class="block w-full h-full object-cover">
        <div class="absolute inset-0 flex flex-col items-center top-100px">
            <div class="text-red-400 text-lg font-bold mb-4 uppercase tracking-widest">Promotion</div>
            <div class="w-640px text-center text-[50px] font-bold text-indigo-950 mb-4">See What Our Clients Say About
                Us</div>
            <div class="carousel-container relative">
                <div ref="emblaRef" class="embla">
                    <div class="embla__container">
                        <div v-for="(item, index) in commentList" :key="index"
                            class="relative min-w-[500px] h-[250px] bg-white rounded-[17px] mt-18 flex items-center justify-center flex-col">
                            <img :src="item.avatar" alt="user"
                                class="absolute object-center pixelated left-1/2 top--60px transform rounded-full -translate-x-1/2 w-[110px] h-[110px] object-cover overflow-hidden">
                            <img :src="DoubleQuotes" alt="double-quotes" class="absolute top-40px left-40px">
                            <div
                                class="w-[393px] h-[114px] text-center text-black text-sm font-normal font-['Poppins'] leading-normal tracking-wide pt-4">
                                {{ item.comment }}
                            </div>
                            <div
                                class="text-center text-black text-sm font-bold font-['Poppins'] leading-normal tracking-wide">
                                {{ item.name }} - {{ item.job }}
                            </div>
                        </div>
                    </div>
                </div>
                <button class="embla__prev" @click="scrollPrev">
                    <i class='bx bx-left-arrow-alt text-white'></i>
                </button>
                <button class="embla__next" @click="scrollNext">
                    <i class='bx bx-right-arrow-alt text-white'></i>
                </button>
            </div>
        </div>
    </div>
</template>
<style scoped>
.demonstration {
    color: var(--el-text-color-secondary);
}

.el-carousel__item h3 {
    color: #475669;
    opacity: 0.75;
    line-height: 150px;
    margin: 0;
    text-align: center;
}

.carousel-container {
    width: 540px;
    overflow: hidden;
    margin: 0 auto;
}

.embla {
    overflow: hidden;
    display: flex;
    justify-content: center;
}

.embla__container {
    display: flex;
    width: 92%;
    gap: 60px;
    padding-left: 30px;
    padding-right: 30px;
}

.embla__slide {
    flex: 0 0 100%;
    min-width: 0;
}

.pixelated {
    image-rendering: pixelated;
}

.embla__prev,
.embla__next {
    position: absolute;
    top: 50%;
    transform: translateY(30%);
    background-color: rgba(0, 0, 0, 0.5);
    border: none;
    outline: none;
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    cursor: pointer;
}

.embla__prev {
    left: 0px; 
}

.embla__next {
    right: 0px;
}

.embla__prev i,
.embla__next i {
    font-size: 24px;
}
</style>