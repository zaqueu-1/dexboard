<template>
    <div class="tracker-container">
        <div class="tracker-header">
            <div class="tracker-header-title">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M6.94383 6.57118C8.3782 5.42193 10.1621 4.79704 12 4.79998C13.9125 4.79998 15.6702 5.46238 17.0562 6.57118L18.3639 5.26348L19.6365 6.53608L18.3288 7.84378C19.2808 9.03551 19.8769 10.4718 20.0486 11.9874C20.2202 13.5029 19.9605 15.0362 19.2993 16.4106C18.638 17.7851 17.6022 18.945 16.3109 19.7567C15.0195 20.5684 13.5253 20.9991 12 20.9991C10.4748 20.9991 8.98051 20.5684 7.6892 19.7567C6.39789 18.945 5.36201 17.7851 4.70078 16.4106C4.03954 15.0362 3.77982 13.5029 3.9515 11.9874C4.12319 10.4718 4.7193 9.03551 5.67123 7.84378L4.36353 6.53698L5.63613 5.26438L6.94383 6.57208V6.57118ZM12 19.2C12.8274 19.2 13.6466 19.037 14.4109 18.7204C15.1753 18.4038 15.8698 17.9398 16.4548 17.3547C17.0398 16.7697 17.5039 16.0752 17.8205 15.3109C18.1371 14.5465 18.3 13.7273 18.3 12.9C18.3 12.0726 18.1371 11.2534 17.8205 10.4891C17.5039 9.72472 17.0398 9.03021 16.4548 8.4452C15.8698 7.86019 15.1753 7.39614 14.4109 7.07953C13.6466 6.76293 12.8274 6.59998 12 6.59998C10.3292 6.59998 8.72674 7.26372 7.54526 8.4452C6.36378 9.62668 5.70003 11.2291 5.70003 12.9C5.70003 14.5708 6.36378 16.1733 7.54526 17.3547C8.72674 18.5362 10.3292 19.2 12 19.2ZM12.9 12H15.6L11.1 17.85V13.8H8.40003L12.9 7.94548V12ZM8.40003 2.09998H15.6V3.89998H8.40003V2.09998Z" fill="#525866"/>
                </svg>
                <p>Rastreador de tempo</p>
            </div>
            <div v-if="records.length > 0" class="historic-btn">
                <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M10 2.5C14.1423 2.5 17.5 5.85775 17.5 10C17.5 14.1423 14.1423 17.5 10 17.5C5.85775 17.5 2.5 14.1423 2.5 10H4C4 13.3135 6.6865 16 10 16C13.3135 16 16 13.3135 16 10C16 6.6865 13.3135 4 10 4C7.9375 4 6.118 5.04025 5.03875 6.625H7V8.125H2.5V3.625H4V5.5C5.368 3.6775 7.54675 2.5 10 2.5ZM10.75 6.25V9.68875L13.1823 12.121L12.121 13.1823L9.25 10.3098V6.25H10.75Z" fill="#525866"/>
                </svg>
                <p>Histórico</p>
            </div>
        </div>
        <div class="tracker-app">
            <div class="tracker-app-header">
                <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M3.89643 14.9513C3.53721 14.9521 3.18422 14.8555 2.87353 14.6713C2.56283 14.4872 2.30556 14.2221 2.128 13.9031C1.95315 13.5864 1.86596 13.2271 1.87574 12.8637C1.88553 12.5002 1.99193 12.1463 2.18355 11.8399L5.82535 5.99866C6.01174 5.68473 6.27638 5.42695 6.59223 5.25166C6.90807 5.07637 7.26381 4.98986 7.62311 5.00095C7.98213 5.00973 8.33241 5.11579 8.63812 5.30827C8.94384 5.50075 9.19399 5.77273 9.36299 6.09638C9.70248 6.75207 9.66005 7.54094 9.25343 8.15644L5.61394 13.9977C5.42938 14.2915 5.1752 14.5329 4.87497 14.6996C4.57473 14.8663 4.23815 14.9529 3.89643 14.9513Z" fill="#F62B54"/>
                <path d="M10.1431 14.951C9.40859 14.951 8.73269 14.5499 8.37777 13.9053C8.20332 13.5894 8.11632 13.231 8.12611 12.8685C8.1359 12.506 8.2421 12.1531 8.43332 11.8476L12.0682 6.01968C12.2518 5.70133 12.5155 5.43897 12.8319 5.25979C13.1483 5.08061 13.5058 4.99115 13.8675 5.00069C14.6082 5.01724 15.2794 5.44044 15.6189 6.10243C15.9561 6.76442 15.9067 7.55802 15.4878 8.17194L11.8537 13.9998C11.6697 14.2923 11.4165 14.5328 11.1176 14.699C10.8186 14.8653 10.4835 14.9519 10.1431 14.951Z" fill="#FFCC00"/>
                <path d="M16.25 15.0001C17.2855 15.0001 18.1249 14.1607 18.1249 13.1252C18.1249 12.0898 17.2855 11.2504 16.25 11.2504C15.2145 11.2504 14.3751 12.0898 14.3751 13.1252C14.3751 14.1607 15.2145 15.0001 16.25 15.0001Z" fill="#00CA72"/>
                </svg>
                <p>Track App</p>
            </div>
            <div class="tracker-app-body">
                <p>AGUARDANDO</p>
                <div class="timer">
                    <p>00:00</p>
                    <p>:00</p>
                </div>
                <div v-if="!recording" class="additional-btns">
                    <svg width="17" height="16" viewBox="0 0 17 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12.9256 8.24962L6.56618 12.4892C6.521 12.5193 6.46851 12.5365 6.41431 12.5391C6.36011 12.5417 6.30622 12.5296 6.25837 12.5039C6.21053 12.4783 6.17054 12.4402 6.14264 12.3937C6.11475 12.3471 6.1 12.2939 6.09998 12.2396V3.76042C6.1 3.70615 6.11475 3.65291 6.14264 3.60636C6.17054 3.55982 6.21053 3.52171 6.25837 3.49609C6.30622 3.47048 6.36011 3.45832 6.41431 3.46091C6.46851 3.46351 6.521 3.48075 6.56618 3.51082L12.9256 7.75042C12.9667 7.77781 13.0004 7.81493 13.0237 7.85847C13.047 7.90201 13.0591 7.95063 13.0591 8.00002C13.0591 8.0494 13.047 8.09802 13.0237 8.14156C13.0004 8.1851 12.9667 8.22222 12.9256 8.24962Z" fill="#FF4A00"/>
                    </svg>
                    <p style="color:#DF1C41;cursor:pointer;" @click="handleRecord('start')">Iniciar</p>
                </div>
                <div v-if="recording"  class="additional-btns">
                    <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M8 14C4.6862 14 2 11.3138 2 8C2 4.6862 4.6862 2 8 2C11.3138 2 14 4.6862 14 8C14 11.3138 11.3138 14 8 14ZM6.2 6.2V9.8H7.4V6.2H6.2ZM8.6 6.2V9.8H9.8V6.2H8.6Z" fill="#0A0D14"/>
                    </svg>
                    <p>Pausar</p>
                    <svg width="1" height="12" viewBox="0 0 1 12" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <line x1="0.5" y1="12" x2="0.5" stroke="#CDD0D5"/>
                    </svg>
                    <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M8 14C4.6862 14 2 11.3138 2 8C2 4.6862 4.6862 2 8 2C11.3138 2 14 4.6862 14 8C14 11.3138 11.3138 14 8 14ZM6.2 6.2V9.8H9.8V6.2H6.2Z" fill="#DF1C41"/>
                    </svg>
                    <p style="cursor:pointer;" @click="handleRecord('stop')">Parar</p>
                </div>
            </div>
            <div v-if="records.length > 0" class="tracker-app-activities">
                <p>TAREFAS ANTERIORES</p>
                <div class="activity">
                    <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <rect x="0.5" y="0.5" width="39" height="39" rx="19.5" fill="white"/>
                    <rect x="0.5" y="0.5" width="39" height="39" rx="19.5" stroke="#E2E4E9"/>
                    <path d="M29.75 18.9164H24.0476L28.9867 16.0652L27.9017 14.1848L22.964 17.0374L25.8138 12.0983L23.9348 11.0133L21.0864 15.951V10.25H18.9136V15.9524L16.0638 11.0133L14.1862 12.0983L17.036 17.036L12.0983 14.1862L11.0133 16.0638L15.9524 18.915H10.25V21.0836H15.951L11.0133 23.9348L12.0983 25.8152L17.036 22.964L14.1848 27.9017L16.0652 28.9867L18.915 24.0476V29.75H21.0836V24.0476L23.9348 28.9867L25.8138 27.9017L22.9626 22.9626L27.9003 25.8138L28.9853 23.9348L24.0476 21.085H29.7486L29.75 18.9164ZM20 22.9501C19.2146 22.9501 18.4614 22.6381 17.9061 22.0828C17.3508 21.5274 17.0388 20.7742 17.0388 19.9889C17.0388 19.2035 17.3508 18.4503 17.9061 17.895C18.4614 17.3396 19.2146 17.0276 20 17.0276C20.7854 17.0276 21.5386 17.3396 22.0939 17.895C22.6492 18.4503 22.9612 19.2035 22.9612 19.9889C22.9612 20.7742 22.6492 21.5274 22.0939 22.0828C21.5386 22.6381 20.7854 22.9501 20 22.9501Z" fill="#625DF5"/>
                    </svg>
                    <div class="activity-inner">
                        <p>Alinhamento - Comercial</p>
                        <span>1:23:05</span>
                    </div>
                    <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M10 3.25C9.38125 3.25 8.875 3.75625 8.875 4.375C8.875 4.99375 9.38125 5.5 10 5.5C10.6187 5.5 11.125 4.99375 11.125 4.375C11.125 3.75625 10.6187 3.25 10 3.25ZM10 14.5C9.38125 14.5 8.875 15.0063 8.875 15.625C8.875 16.2437 9.38125 16.75 10 16.75C10.6187 16.75 11.125 16.2437 11.125 15.625C11.125 15.0063 10.6187 14.5 10 14.5ZM10 8.875C9.38125 8.875 8.875 9.38125 8.875 10C8.875 10.6188 9.38125 11.125 10 11.125C10.6187 11.125 11.125 10.6188 11.125 10C11.125 9.38125 10.6187 8.875 10 8.875Z" fill="#525866"/>
                    </svg>
                </div>
                <div class="activity">
                    <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <rect x="0.5" y="0.5" width="39" height="39" rx="19.5" fill="white"/>
                    <rect x="0.5" y="0.5" width="39" height="39" rx="19.5" stroke="#E2E4E9"/>
                    <circle cx="20" cy="20" r="10.5" fill="#00A82D"/>
                    <path d="M17.525 16.2833C17.525 16.4176 17.5141 16.6415 17.3831 16.787C17.2413 16.9213 17.023 16.9325 16.892 16.9325C16.1553 16.9325 15.1334 16.7473 14.4365 17.0332C15.5 15.125 17.5602 13.857 17.5468 13.9663C17.4487 14.7214 17.525 15.5238 17.525 16.2833ZM19.7295 24.9466C19.7295 24.0176 20.4716 23.2565 21.3883 23.2565C21.6612 23.2565 21.8794 23.4803 21.8794 23.7602C21.8794 23.9504 21.7812 24.1071 21.6284 24.1967C21.462 24.2991 21.2316 24.2513 21.0828 24.387C20.9736 24.4765 20.8863 24.622 20.8863 24.7787C20.8863 24.9466 20.9518 25.1033 21.0609 25.2152C21.2574 25.4167 21.5193 25.5286 21.803 25.5286C22.5452 25.5286 23.1454 24.913 23.1454 24.1519C23.1454 23.4691 22.6979 22.8647 22.1086 22.5961C21.2142 22.1375 19.8458 22.3985 19.7404 20.9619C19.5764 21.7217 19.2145 23.0774 18.2344 23.0774C15.2735 23.2578 14.2063 20.8594 14 18.3204C14 17.7719 14.3274 17.4026 14.7421 17.3466C15.4842 17.3466 16.2263 17.3466 16.9684 17.3466C17.3504 17.3466 17.5687 17.2459 17.7105 17.1116C17.8961 16.9325 17.9397 16.675 17.9397 16.3728C17.9397 15.5856 17.9397 14.375 17.9397 14.0111C17.9397 13.5359 18.3544 13.25 18.8892 13.25C19.2042 13.25 19.4998 13.2611 19.8059 13.3395C20.4716 13.5074 20.6135 14.2014 20.6135 14.2014C20.6135 14.2014 21.8685 14.4253 22.5015 14.5372C23.1017 14.6491 24.5859 14.7499 24.8697 16.2833C25.5354 19.9322 25.1316 23.4691 25.0989 23.4691C24.6296 26.9166 21.8358 26.7487 21.8358 26.7487C20.8202 26.7487 19.7295 26.0556 19.7295 24.9466ZM23.0035 19.0032C22.6434 18.9696 22.3378 19.1151 22.2287 19.3949C22.074 19.7915 23.6692 20.1212 23.6692 19.574C23.6256 19.2606 23.3637 19.0479 23.0035 19.0032Z" fill="white"/>
                    </svg>
                    <div class="activity-inner">
                        <p>Dashboard - Redesign</p>
                        <span>3:14:26</span>
                    </div>
                    <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M10 3.25C9.38125 3.25 8.875 3.75625 8.875 4.375C8.875 4.99375 9.38125 5.5 10 5.5C10.6187 5.5 11.125 4.99375 11.125 4.375C11.125 3.75625 10.6187 3.25 10 3.25ZM10 14.5C9.38125 14.5 8.875 15.0063 8.875 15.625C8.875 16.2437 9.38125 16.75 10 16.75C10.6187 16.75 11.125 16.2437 11.125 15.625C11.125 15.0063 10.6187 14.5 10 14.5ZM10 8.875C9.38125 8.875 8.875 9.38125 8.875 10C8.875 10.6188 9.38125 11.125 10 11.125C10.6187 11.125 11.125 10.6188 11.125 10C11.125 9.38125 10.6187 8.875 10 8.875Z" fill="#525866"/>
                    </svg>
                </div>
            </div>
            <div v-if="records.length <= 0" class="tracker-app-empty">
                <IconNoActivity />
                <p>Sem registro de atividades</p>
            </div>
        </div>

    </div>
</template>

<script>
import { ref } from 'vue'
import IconNoActivity from './icons/IconNoActivity.vue'

export default {
    name: 'TimeTracker',
    components: {
        IconNoActivity,
    },
    props: {

    },
    setup() {
        let records = ref([])
        let recording = ref(false)

        const handleRecord = (type) => {
            recording.value = !recording.value

            if (type === 'stop') {
                records.value.push(1)
            }
        }

        return {
            records,
            recording,
            handleRecord
        }
    },

}
</script>

<style lang="scss" scoped>
@use 'assets/scss/main';

.tracker-container {
    @include main.tall-container();
}

.tracker-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 320px;
    margin-top: -.75rem;
    p {
        @include main.text-header();
        color: main.$text-main-900;
    }
    .historic-btn {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: .5rem;
        height: 32px;
        width: 104px;
        border-radius: 8px;
        border: 1px solid main.$soft-200;
        background-color: white;
        cursor: pointer;
        p {
            @include main.text-main();
            color: main.$text-sub-500;
        }
    }

    .tracker-header-title {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: .5rem;
        p {
            @include main.text-header();
            color: main.$text-main-900;
        }
    
    }
}

.tracker-app {
    margin-top: 1rem;
}
.tracker-app-header {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    gap: .5rem;
    width: 320px;
    height: 32px;
    background-color: main.$bg-weak-100;
    border: 1px solid main.$soft-200;
    padding: 0px 10px 0px 12px;
    border-radius: 16px 16px 0 0;
    p {
        @include main.text-main();
        color: main.$text-sub-500;
    }
}

.tracker-app-body {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 8px 10px 8px 12px;
    height: 126px;
    width: 320px;
    border: 1px solid main.$soft-200;
    border-radius: 0 0 16px 16px;
    p {
        @include main.text-main();
        color: main.$soft-400;
        font-size: 11px;
        line-height: 12px;
        letter-spacing: 2%;
    }
}

.timer {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: -2.5rem;
    p {
        @include main.text-main();
        color: main.$text-main-900;
        font-size: 40px;
        line-height: 48px;
        letter-spacing: -1%;
        &:last-of-type {
            color: main.$soft-400;
        }
    }
}

.additional-btns {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    margin-top: -2.5rem;
    width: 288px;
    svg:first-child {
        margin-right: -.75rem;
    }
    svg:last-of-type {
        margin-right: -.75rem;
    }
    p {
        @include main.text-soft();
        color: main.$text-main-900;
        &:last-of-type {
            color: main.$color-primary-base
        }
    }
}

.tracker-app-activities {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
    margin-top: .5rem;
    width: 320px;
    height: 122px;
    gap: .5rem;
    p {
        @include main.text-main();
        color: main.$soft-400;
        font-size: 11px;
        line-height: 12px;
        letter-spacing: 2%;
    }
}

.activity {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    width: 320px;
    margin-top: 0;
    .activity-inner {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: flex-start;
        width: 100%;
        p {
            margin-top: 0;
            @include main.text-main();
            color: main.$text-main-900;
            font-weight: 400;
        }
        span {
            @include main.text-main();
            font-weight: 400;
            color: main.$text-sub-500;
            font-size: 12px;
            line-height: 16px;
            margin-top: -.75rem;
        }
    }
}

.tracker-app-empty {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-top: 1.5rem;
    p {
        @include main.text-main();
        color: main.$soft-400;
        font-weight: 400;
    }
}
</style>