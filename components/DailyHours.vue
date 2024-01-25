<template>
    <div class="daily-container">
        <div class="daily-header">
            <div class="daily-header-title">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M17.0562 6.57118L18.3639 5.26348L19.6365 6.53608L18.3288 7.84377C19.621 9.46123 20.2448 11.5121 20.0722 13.5751C19.8995 15.6381 18.9435 17.5567 17.4004 18.9369C15.8574 20.3171 13.8444 21.0541 11.775 20.9964C9.70555 20.9388 7.73671 20.091 6.27283 18.6271C4.80895 17.1633 3.96114 15.1944 3.90353 13.125C3.84592 11.0555 4.58288 9.04259 5.96306 7.49953C7.34323 5.95648 9.26185 5.00045 11.3249 4.8278C13.3879 4.65515 15.4388 5.27898 17.0562 6.57118ZM12 19.2C12.8273 19.2 13.6466 19.037 14.4109 18.7204C15.1753 18.4038 15.8698 17.9398 16.4548 17.3547C17.0398 16.7697 17.5038 16.0752 17.8204 15.3109C18.1371 14.5465 18.3 13.7273 18.3 12.9C18.3 12.0726 18.1371 11.2534 17.8204 10.4891C17.5038 9.72472 17.0398 9.03021 16.4548 8.4452C15.8698 7.86019 15.1753 7.39614 14.4109 7.07953C13.6466 6.76293 12.8273 6.59998 12 6.59998C10.3291 6.59998 8.72671 7.26372 7.54523 8.4452C6.36375 9.62668 5.7 11.2291 5.7 12.9C5.7 14.5708 6.36375 16.1733 7.54523 17.3547C8.72671 18.5362 10.3291 19.2 12 19.2ZM11.1 8.39997H12.9V13.8H11.1V8.39997ZM8.4 2.09998H15.6V3.89998H8.4V2.09998Z" fill="#525866"/>
                </svg>
                <p>Horas diárias de trabalho</p>
            </div>
            <div class="details-btn">
                <p @click="handleDetails">Detalhes</p>
            </div>
        </div>
        <div class="divider"></div>
        <div class="daily-app">
            <div class="daily-time">
                <p>{{ details ? hours : 0 }}</p>
                <span>horas</span>
                <p>{{ details ? minutes : 0 }}</p>
                <span>minutos</span>
                <span>no</span>
                <span>total ⏳</span>
            </div>
            <div class="daily-track">
                <svg :width="details ? 72 : 103" height="10" :viewBox="details ? '0 0 72 10' : '0 0 103 10'" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect :width="details ? 72 : 103" height="10" rx="2" :fill="details ? '#F2AE40' :'#E2E4E9'"/>
                </svg>
                <svg :width="details ? 188 : 103" height="10" :viewBox="details ? '0 0 188 10' : '0 0 103 10'" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect :width="details ? 188 : 103" height="10" rx="2" :fill="details ? '#35B9E9' :'#E2E4E9'"/>
                </svg>
                <svg :width="details ? 48 : 103" :viewBox="details ? '0 0 48 10' : '0 0 103 10'" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect :width="details ? 48 : 103" height="10" rx="2" :fill="details ? '#6E3FF3' :'#E2E4E9'"/>
                </svg>
            </div>
            <div class="daily-subtitle">
                <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g clip-path="url(#clip0_2_74058)">
                <g filter="url(#filter0_d_2_74058)">
                <circle cx="8" cy="8" r="6" :fill="details ? '#F2AE40' :'#CDD0D5'"/>
                <circle cx="8" cy="8" r="5" stroke="white" stroke-width="2"/>
                </g>
                </g>
                <defs>
                <filter id="filter0_d_2_74058" x="-2" y="0" width="20" height="20" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                <feFlood flood-opacity="0" result="BackgroundImageFix"/>
                <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
                <feOffset dy="2"/>
                <feGaussianBlur stdDeviation="2"/>
                <feColorMatrix type="matrix" values="0 0 0 0 0.105882 0 0 0 0 0.109804 0 0 0 0 0.113725 0 0 0 0.04 0"/>
                <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_2_74058"/>
                <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_2_74058" result="shape"/>
                </filter>
                <clipPath id="clip0_2_74058">
                <rect width="16" height="16" fill="white"/>
                </clipPath>
                </defs>
                </svg>
                <p :style="details ? 'color:#525866' : ''">Descanso</p>
                <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g clip-path="url(#clip0_2_74058)">
                <g filter="url(#filter0_d_2_74058)">
                <circle cx="8" cy="8" r="6" :fill="details ? '#35B9E9' :'#CDD0D5'"/>
                <circle cx="8" cy="8" r="5" stroke="white" stroke-width="2"/>
                </g>
                </g>
                <defs>
                <filter id="filter0_d_2_74058" x="-2" y="0" width="20" height="20" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                <feFlood flood-opacity="0" result="BackgroundImageFix"/>
                <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
                <feOffset dy="2"/>
                <feGaussianBlur stdDeviation="2"/>
                <feColorMatrix type="matrix" values="0 0 0 0 0.105882 0 0 0 0 0.109804 0 0 0 0 0.113725 0 0 0 0.04 0"/>
                <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_2_74058"/>
                <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_2_74058" result="shape"/>
                </filter>
                <clipPath id="clip0_2_74058">
                <rect width="16" height="16" fill="white"/>
                </clipPath>
                </defs>
                </svg>
                <p :style="details ? 'color:#525866' : ''">Ativo</p>
                <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                <g clip-path="url(#clip0_2_74058)">
                <g filter="url(#filter0_d_2_74058)">
                <circle cx="8" cy="8" r="6" :fill="details ? '#6E3FF3' :'#CDD0D5'"/>
                <circle cx="8" cy="8" r="5" stroke="white" stroke-width="2"/>
                </g>
                </g>
                <defs>
                <filter id="filter0_d_2_74058" x="-2" y="0" width="20" height="20" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
                <feFlood flood-opacity="0" result="BackgroundImageFix"/>
                <feColorMatrix in="SourceAlpha" type="matrix" values="0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 127 0" result="hardAlpha"/>
                <feOffset dy="2"/>
                <feGaussianBlur stdDeviation="2"/>
                <feColorMatrix type="matrix" values="0 0 0 0 0.105882 0 0 0 0 0.109804 0 0 0 0 0.113725 0 0 0 0.04 0"/>
                <feBlend mode="normal" in2="BackgroundImageFix" result="effect1_dropShadow_2_74058"/>
                <feBlend mode="normal" in="SourceGraphic" in2="effect1_dropShadow_2_74058" result="shape"/>
                </filter>
                <clipPath id="clip0_2_74058">
                <rect width="16" height="16" fill="white"/>
                </clipPath>
                </defs>
                </svg>
                <p :style="details ? 'color:#525866' : ''">Hora extra</p>
            </div>

        </div>

    </div>
</template>

<script>
import { ref } from 'vue'

export default {
    name: 'DailyHours',
    components: {

    },
    props: {

    },
    setup() {
        let hours = ref(12)
        let minutes = ref(27)
        let details = ref(false)

        const handleDetails = () => {
            details.value = !details.value
        }

        return {
            hours,
            minutes,
            details,
            handleDetails,
        }
    },


}

</script>

<style lang="scss" scoped>
@use 'assets/scss/main';

.daily-container {
    @include main.small-container();
}

.daily-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 320px;
    margin-top: -.5rem;
    p {
        @include main.text-header();
        color: main.$text-main-900;
    }
    .details-btn {
        display: flex;
        align-items: center;
        justify-content: center;
        height: 32px;
        width: 79px;
        padding: 0 6px;
        border-radius: 8px;
        border: 1px solid main.$soft-200;
        background-color: white;
        cursor: pointer;
        p {
            @include main.text-main();
            color: main.$text-sub-500;
        }
    }

    .daily-header-title {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: .5rem;
        p {
            @include main.text-main();
            color: main.$text-sub-500;
        }
    }
}


.divider {
    @include main.divider();
    margin-top: .5rem;
}

.daily-app {
    display: flex;
    align-items: center;
    flex-direction: column;
    .daily-time {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        width: 320px;
        gap: .25rem;
        p {
            @include main.text-header();
            color: main.$text-main-900;
            letter-spacing: -1.1%;
        }
        span {
            @include main.text-header();
            color: main.$text-sub-500;
            letter-spacing: -1.1%;
            font-weight: 400;
        }
    }
    .daily-track {
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: 320px;
        margin-top: .5rem;
    }
    .daily-subtitle {
        display: flex;
        width: 320px;
        margin-top: .5rem;
        align-items: center;
        justify-content: flex-start;
        gap: .5rem;
        p {
            @include main.text-sub();
            color: main.$text-disabled-300;
        }
    }
}

</style>