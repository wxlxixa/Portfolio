<template>
    <div class="">
        <h3 class="w-full text-center text-3xl dark:text-[#d9d9d9] border-t border-b border-black dark:border-gray-300 py-4 uppercase font-semibold">portfolio</h3>
    </div>
    <div class="max-w-5xl xl:max-w-6xl mx-auto pt-12 px-[2%] pb-8 lg:my-[200px]">
        <!-- 카테고리 -->
        <div class="w-full mx-auto mt-8">
            <ul class="flex flex-wrap">
                <li class="border darkMode bg-white mr-3 mb-2 rounded-md">
                    <button @click="CateName = '전체'" :class="CateName === '전체' && 'text-lime-600 dark:text-lime-400'" class="text-xs py-2 px-5 lg:text-lg">전체</button>
                </li>
                <li class="border darkMode bg-white mr-3 mb-2 rounded-md" v-for="e in CateList" :key="e">
                    <button @click="CateName = e.type" :class="CateName === e.type && 'text-lime-800'" class="text-xs py-2 px-2 lg:text-lg lg:py-3 lg:px-4">{{ e.type }}</button>
                </li>
            </ul>
        </div>
        <div class=""></div>
        <!-- 
            contents 
        -->
        <div class="w-full lg:max-w-7xl mx-auto mt-8">
            <swiper :pagination="{type: 'progressbar',}" :navigation="true" :modules="modules" :keyboard="true" :cssMode="true" class="mySwiper">
                <swiper-slide v-for="e in CateItem" :key="e">
                    <div class="bg-white mb-8 pt-12 group px-8 pb-16 rounded-md flex border darkMode flex-wrap">
                <div class="md:basis-[48%] lg:basis-[40%] relative mx-auto items-center flex">
                    <!-- img  -->
                    <img class="w-full" :src="require(`@/assets/images/${e.img}`)">
                </div>
                <div class="basis-full md:basis-[52%] pt-10">
                    <h3 class="text-2xl font-bold pt-[10px] pb-[10px] md:pl-[50px]">
                        {{ e.descTitle }}
                    </h3>
                    <p class="text-sm pt-[10px] pb-[10px] md:pl-[50px]">{{ e.desc }}</p>
                    <p class="text-sm pt-[10px] pb-[10px] md:pl-[50px]">키워드 : <span v-for="el in e.keyword" :key="el" class="mr-2 align-middle">{{ el }}</span> </p>
                    <p class="text-sm pt-[10px] pb-[10px] md:pl-[50px]">사용툴 : <span v-for="el in e.tools" :key="el" class="mr-2 align-middle">{{ el }}</span> </p>
                    <p class="text-sm pt-[10px] pb-[10px] md:pl-[50px]">작업기간 : {{ e.date }}</p>
                    <!-- <p class="text-sm pt-[10px] pb-[10px] md:pl-[50px]">기여도 : {{ e.contribution }}</p> -->
                    <ul class="flex justify-center mt-6">
                        <!-- site -->
                        <li v-if="e.Site"><a :href="e.Site" class="py-1 px-8 border rounded-md darkMode text-sm lg:text-lg lg:py-2">Site</a></li>
                        <!-- notion -->
                        <li v-if="e.Notion"><a :href="e.Notion" :class="e.Notion === '' && 'hidden'" class="py-1 px-5 border rounded-md darkMode text-sm mx-4 lg:text-lg lg:py-2" target="_blank">Notion</a></li>
                        <!-- github -->
                        <li v-if="e.GitHub"><a :href="e.GitHub" :class="e.GitHub === '' && 'hidden'" class="py-1 px-5 border rounded-md darkMode text-sm lg:text-lg lg:py-2" target="_blank">GitHub</a></li>
                        <!-- <li v-if="e.redesign"><a :href="e.redesign" :class="e.redesign === '' && 'hidden'" class="py-1 px-8 border rounded-md darkMode text-sm" target="_blank">{{ e.type === 'Publishing' ? 'Clone' : 'Redesign' }}</a></li> -->
                    </ul>
                </div>
            </div>
                </swiper-slide>
            </swiper>
        </div>
    </div>
</template>
<script>
// import Title from '../components/Title.vue'
// import PortfolioData from '../assets/Portfolio.json'

import { Swiper, SwiperSlide } from 'swiper/vue';
import { EffectFade, Pagination, Autoplay, Navigation, Keyboard } from 'swiper';
import 'swiper/css'
import 'swiper/css/bundle';
import 'swiper/css/pagination';
import "swiper/css/effect-fade";
import 'swiper/css/navigation';

export default {
    name: "PortfolioPage",
    data() {
        return {
            CateName: "전체",
            modules: [EffectFade, Pagination, Autoplay, Navigation, Keyboard],
            // Portfolio : PortfolioData,
            WorkList: [
                {
                    "img" : "pds.png",
                    "descTitle" : "택배 조회 서비스",
                    "desc" : "스마트 택배 조회 api를 활용한 제작한 국내/외 웹앱",
                    "keyword": ["#반응형", "#다크모드"],
                    "tools" : ["Vue.js3", "TailwindCSS"],
                    "date" : "14일",
                    "contribution" : "100%",
                    "type" : "Publishing",
                    "Site" : "https://jeonmin-a.github.io/DeliveryTracking/",
                    "Notion" : "https://jeonmin-a.notion.site/273672f798b644e193c86c6034dffdf0",
                    "GitHub" : "https://github.com/JeonMin-A/DeliveryTracking_src",
                },
                {
                    "img" : "calculator.png",
                    "descTitle" : "퍼센테이지 계산기",
                    "desc" : "계산기 웹앱",
                    "keyword": ["#반응형", "#다크모드"],
                    "tools" : ["Vue.js3", "TailwindCSS"],
                    "date" : "7일",
                    "contribution" : "100%",
                    "type" : "Publishing",
                    "Site" : "https://jeonmin-a.github.io/Calculator-percentage/",
                    "Notion" : "https://jeonmin-a.notion.site/d318be19ac354114b909b43701ef8d8d?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/Calculator-percentage",
                },
                {
                    "img" : "Quiz.png",
                    "descTitle" : "Quiz",
                    "desc" : "HTML, CSS, JavaScript에 관한 퀴즈",
                    "keyword": ["#반응형"],
                    "tools" : ["Vue.js3", "TailwindCSS"],
                    "date" : "7일",
                    "contribution" : "100%",
                    "type" : "Publishing",
                    "Site" : "https://jeonmin-a.github.io/Quiz/",
                    "Notion" : "https://jeonmin-a.notion.site/Quiz-10248b404da946ae916a2af7f463007a?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/Quiz_src",
                },
                {
                    "img" : "ilsangtrip.png",
                    "descTitle" : "일상과 여행",
                    "desc" : "클론코딩",
                    "keyword": ["#인스타그램API"],
                    "tools" : ["Vue.js3", "SCSS", "Instagram Api"],
                    "date" : "12일",
                    "contribution" : "100%",
                    "type" : "CloneCode",
                    "Site" : "https://clone-code-ilsangtrip.vercel.app/",
                    "Notion" : "https://jeonmin-a.notion.site/4152a2c60d5d4d29be665bc275f7abe0?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/-CloneCode-ilsangtrip",
                },
                {
                    "img" : "waterwork.png",
                    "descTitle" : "대구광역시 상수도사업본부",
                    "desc" : "사이트 리디자인",
                    "keyword": ["#반응형"],
                    "tools" : ["Vue.js3", "TailwindCSS"],
                    "date" : "5일",
                    "contribution" : "100%",
                    "type" : "Redisign",
                    "Site" : "https://water-work.vercel.app/",
                    "Notion" : "https://jeonmin-a.notion.site/0c7e5febcb9b4b8594d61ad70e9151bb?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/water-work",
                },
                {
                    "img" : "template.png",
                    "descTitle" : "홈페이지 탬플릿",
                    "desc" : "사이트 구축",
                    "keyword": ["#반응형", "#파이어베이스", "#로그인 #게시판 구축"],
                    "tools" : ["Vue.js3", "TailwindCSS", "FireBase"],
                    "date" : "30일",
                    "contribution" : "100%",
                    "type" : "WepApp",
                    "Site" : "https://template-home-page.vercel.app/",
                    "Notion" : "https://jeonmin-a.notion.site/6902eb144e684916a0bce5245448520c?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/template-HomePage",
                },
                {
                    "img" : "nongdal.png",
                    "descTitle" : "농달 프로젝트",
                    "desc" : "농림축산 데이터를 활용해 제작한 사이트",
                    "keyword": ["#반응형", "#FireBase", "#공모전"],
                    "tools" : ["Vue.js3", "TailwindCSS", "FireBase", "Git", "Figma"],
                    "date" : "14일",
                    "contribution" : "40%",
                    "type" : "TeamProject",
                    "Site" : "https://food-two-pi.vercel.app/",
                    "Notion" : "https://trusting-join-924.notion.site/dbe74906f0e34ebc8fe42b54ddc48857?pvs=4",
                    "GitHub" : "https://github.com/KwonHyeokGeon/food",
                },
                {
                    "img" : "IKMO.png",
                    "descTitle" : "IKMO (진행형)",
                    "desc" : "마구마구 게임 유저들을 위한 실시간 경기 조회",
                    "keyword": ["#게임", "#백엔드"],
                    "tools" : ["JavaScript", "CSS", "Figma"],
                    "date" : "30일",
                    "contribution" : "70%",
                    "type" : "TeamProject",
                    "Site" : "https://jeonmin-a.github.io/Quiz/",
                    "Notion" : "https://jeonmin-a.notion.site/IKMO-c5aa35d5f0a3490da2bb057c4999c03d?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/Quiz_src",
                },
                {
                    "img" : "group.png",
                    "descTitle" : "근처 모임 찾기 (진행형) ",
                    "desc" : "근처 모임이나 동호회를 찾아 볼 수 있는 사이트",
                    "keyword": ["#웹앱"],
                    "tools" : ["JavaScript", "CSS", "Figma"],
                    "date" : "30일",
                    "contribution" : "60%",
                    "type" : "TeamProject",
                    "Site" : "https://jeonmin-a.github.io/Quiz/",
                    "Notion" : "https://jeonmin-a.notion.site/30121599f8e34cfeaa198e6ee1af51b0?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/Quiz_src",
                },
                {
                    "img" : "selena.png",
                    "descTitle" : "삼성 영여 셀레나",
                    "desc" : "클론코딩",
                    "keyword": ["#웹앱"],
                    "tools" : ["HTML5", "CSS3"],
                    "date" : "14일",
                    "contribution" : "60%",
                    "type" : "CloneCode",
                    "Site" : "https://clone-code-samsung-selena.vercel.app/",
                    "Notion" : "https://jeonmin-a.notion.site/4d647c823ad449d8b0ea6fe2fd388b3a?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/-CloneCode-samsung_selena",
                },
                {
                    "img" : "portfolio.png",
                    "descTitle" : "Portfolio",
                    "desc" : "개인 포트폴리오 사이트",
                    "keyword": ["#웹앱"],
                    "tools" : ["Vue.js", "TailwindCSS", "Figma", "vercel"],
                    "date" : "3일",
                    "contribution" : "100%",
                    "type" : "WepApp",
                    "Site" : "https://portfolio-swart-three-35.vercel.app/",
                    "Notion" : "https://jeonmin-a.notion.site/3dbb235d1e8246d89932b67cf5db31d8?pvs=4",
                    "GitHub" : "https://github.com/JeonMin-A/Portfolio",
                },
            ]
        }
    },
    components:{
        Swiper,
        SwiperSlide
    },
    computed:{
        CateItem(){
            return this.WorkList.filter((data)=>{
            if(this.CateName !== '전체'){
                return data.type === this.CateName
            }else{
                return data.type
            }
        })
    },
    CateList(){
        return this.WorkList.filter((item,i)=>{
            return(
                this.WorkList.findIndex((item2)=>{
                    return item.type === item2.type
            }) === i
        )
        })
    },
    },
}
</script>
<style>
    .swiper-button-prev{
        /* border: 1px solid black; */
        border-radius: 50%;
        width: 50px;
        height: 50px;
    }
    .swiper-button-prev::after{
        content: '';
        /* background-image: url("data:image/svg+xml,%3Csvg width='24' height='24' fill='%23000' xmlns='http://www.w3.org/2000/svg' fill-rule='evenodd' clip-rule='evenodd'%3E%3Cpath d='M20 .755l-14.374 11.245 14.374 11.219-.619.781-15.381-12 15.391-12 .609.755z'/%3E%3C/svg%3E"); */
        background-size: cover;
        width: 25px;
        height: 25px;
        left: 14px;
    }
    .swiper-button-next{
        /* border: 1px solid black; */
        border-radius: 50%;
        width: 50px;
        height: 50px;
    }
    .swiper-button-next::after{
        content: '';
        /* background-image: url("data:image/svg+xml,%3Csvg width='24' height='24' fill='%23000' xmlns='http://www.w3.org/2000/svg' fill-rule='evenodd' clip-rule='evenodd'%3E%3Cpath d='M4 .755l14.374 11.245-14.374 11.219.619.781 15.381-12-15.391-12-.609.755z'/%3E%3C/svg%3E"); */
        background-size: cover;
        width: 25px;
        height: 25px;
        right: 20px;
    }

    .swiper-pagination-progressbar-fill {
        border: 2px solid lightgray;
        border-radius: 5px;
    }

    .swiper-pagination-progressbar {
        background-color: lightgrey;
        border-radius: 5px;
    }
    
</style>