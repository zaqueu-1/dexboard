<template>
    <div class="tracker-container">
        <div class="tracker-header">
            <div class="tracker-header-title">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M6.94383 6.57118C8.3782 5.42193 10.1621 4.79704 12 4.79998C13.9125 4.79998 15.6702 5.46238 17.0562 6.57118L18.3639 5.26348L19.6365 6.53608L18.3288 7.84378C19.2808 9.03551 19.8769 10.4718 20.0486 11.9874C20.2202 13.5029 19.9605 15.0362 19.2993 16.4106C18.638 17.7851 17.6022 18.945 16.3109 19.7567C15.0195 20.5684 13.5253 20.9991 12 20.9991C10.4748 20.9991 8.98051 20.5684 7.6892 19.7567C6.39789 18.945 5.36201 17.7851 4.70078 16.4106C4.03954 15.0362 3.77982 13.5029 3.9515 11.9874C4.12319 10.4718 4.7193 9.03551 5.67123 7.84378L4.36353 6.53698L5.63613 5.26438L6.94383 6.57208V6.57118ZM12 19.2C12.8274 19.2 13.6466 19.037 14.4109 18.7204C15.1753 18.4038 15.8698 17.9398 16.4548 17.3547C17.0398 16.7697 17.5039 16.0752 17.8205 15.3109C18.1371 14.5465 18.3 13.7273 18.3 12.9C18.3 12.0726 18.1371 11.2534 17.8205 10.4891C17.5039 9.72472 17.0398 9.03021 16.4548 8.4452C15.8698 7.86019 15.1753 7.39614 14.4109 7.07953C13.6466 6.76293 12.8274 6.59998 12 6.59998C10.3292 6.59998 8.72674 7.26372 7.54526 8.4452C6.36378 9.62668 5.70003 11.2291 5.70003 12.9C5.70003 14.5708 6.36378 16.1733 7.54526 17.3547C8.72674 18.5362 10.3292 19.2 12 19.2ZM12.9 12H15.6L11.1 17.85V13.8H8.40003L12.9 7.94548V12ZM8.40003 2.09998H15.6V3.89998H8.40003V2.09998Z" fill="#525866"/>
                </svg>
                <p>Time tracker</p>
            </div>
            <div v-if="loadTasks" class="historic-btn">
                <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M10 2.5C14.1423 2.5 17.5 5.85775 17.5 10C17.5 14.1423 14.1423 17.5 10 17.5C5.85775 17.5 2.5 14.1423 2.5 10H4C4 13.3135 6.6865 16 10 16C13.3135 16 16 13.3135 16 10C16 6.6865 13.3135 4 10 4C7.9375 4 6.118 5.04025 5.03875 6.625H7V8.125H2.5V3.625H4V5.5C5.368 3.6775 7.54675 2.5 10 2.5ZM10.75 6.25V9.68875L13.1823 12.121L12.121 13.1823L9.25 10.3098V6.25H10.75Z" fill="#525866"/>
                </svg>
                <p @click="handleHistory">History</p>
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
                <p>WAITING</p>
                <div class="timer">
                    <p>{{ hours < 10 ? '0'+hours : hours }}</p>
                    <p>:{{ minutes < 10 ? '0'+minutes : minutes }}</p>
                    <p>:{{ seconds < 10 ? '0'+seconds : seconds }}</p>
                </div>
                <div v-if="!recording" class="additional-btns">
                    <svg width="17" height="16" viewBox="0 0 17 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M12.9256 8.24962L6.56618 12.4892C6.521 12.5193 6.46851 12.5365 6.41431 12.5391C6.36011 12.5417 6.30622 12.5296 6.25837 12.5039C6.21053 12.4783 6.17054 12.4402 6.14264 12.3937C6.11475 12.3471 6.1 12.2939 6.09998 12.2396V3.76042C6.1 3.70615 6.11475 3.65291 6.14264 3.60636C6.17054 3.55982 6.21053 3.52171 6.25837 3.49609C6.30622 3.47048 6.36011 3.45832 6.41431 3.46091C6.46851 3.46351 6.521 3.48075 6.56618 3.51082L12.9256 7.75042C12.9667 7.77781 13.0004 7.81493 13.0237 7.85847C13.047 7.90201 13.0591 7.95063 13.0591 8.00002C13.0591 8.0494 13.047 8.09802 13.0237 8.14156C13.0004 8.1851 12.9667 8.22222 12.9256 8.24962Z" fill="#FF4A00"/>
                    </svg>
                    <p style="color:#DF1C41;cursor:pointer;" @click="startTimer">Start</p>
                </div>
                <div v-if="recording"  class="additional-btns">
                    <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M8 14C4.6862 14 2 11.3138 2 8C2 4.6862 4.6862 2 8 2C11.3138 2 14 4.6862 14 8C14 11.3138 11.3138 14 8 14ZM6.2 6.2V9.8H7.4V6.2H6.2ZM8.6 6.2V9.8H9.8V6.2H8.6Z" fill="#0A0D14"/>
                    </svg>
                    <p v-if="!paused" style="cursor:pointer;" @click="pauseTimer">Pause</p>
                    <p v-else style="cursor:pointer;" @click="startTimer">Resume</p>
                    <svg width="1" height="12" viewBox="0 0 1 12" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <line x1="0.5" y1="12" x2="0.5" stroke="#CDD0D5"/>
                    </svg>
                    <svg width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M8 14C4.6862 14 2 11.3138 2 8C2 4.6862 4.6862 2 8 2C11.3138 2 14 4.6862 14 8C14 11.3138 11.3138 14 8 14ZM6.2 6.2V9.8H9.8V6.2H6.2Z" fill="#DF1C41"/>
                    </svg>
                    <p style="cursor:pointer;" @click="stopTimer">Stop</p>
                </div>
            </div>
            <div v-if="loadTasks && previousTasks.length > 0" class="tracker-app-activities">
                <p>PREVIOUS TASKS</p>
                <div class="activity" v-for="(task,index) in previousTasks.slice(0,2)" :key="index">
                    <IconLoom v-if="task.icon == 'loom'"/>
                    <IconEvernote v-if="task.icon == 'evernote'"/>
                    <div class="activity-inner">
                        <p>{{ task.title }}</p>
                        <span>{{ task.time }}</span>
                    </div>
                    <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M10 3.25C9.38125 3.25 8.875 3.75625 8.875 4.375C8.875 4.99375 9.38125 5.5 10 5.5C10.6187 5.5 11.125 4.99375 11.125 4.375C11.125 3.75625 10.6187 3.25 10 3.25ZM10 14.5C9.38125 14.5 8.875 15.0063 8.875 15.625C8.875 16.2437 9.38125 16.75 10 16.75C10.6187 16.75 11.125 16.2437 11.125 15.625C11.125 15.0063 10.6187 14.5 10 14.5ZM10 8.875C9.38125 8.875 8.875 9.38125 8.875 10C8.875 10.6188 9.38125 11.125 10 11.125C10.6187 11.125 11.125 10.6188 11.125 10C11.125 9.38125 10.6187 8.875 10 8.875Z" fill="#525866"/>
                    </svg>
                </div>
            </div>
            <div v-if="!loadTasks" class="tracker-app-empty">
                <IconNoActivity />
                <p>No activity record</p>
            </div>
        </div>
    </div>
</template>

<script>
import { ref } from 'vue'
import IconNoActivity from './icons/IconNoActivity.vue'
import IconEvernote from './icons/IconEvernote.vue'
import IconLoom from './icons/IconLoom.vue'

export default {
    name: 'TimeTracker',
    components: {
    IconNoActivity,
    IconEvernote,
    IconLoom
},
    props: {
        previousTasks: {
            type: Array,
        }
    },
    setup(props, { emit }) {
        let recording = ref(false)
        let paused = ref(false)
        let timer = null
        let seconds = ref(0)
        let minutes = ref(0)
        let hours = ref(0)

        let loadTasks = ref(false)

        onMounted(() => {
            props.previousTasks ? loadTasks.value = true : loadTasks.value = false
        })

        const startTimer = () => {
            recording.value = true
            paused.value = false

            timer = setInterval(() => {
                seconds.value++
                if (seconds.value === 60) {
                    seconds.value = 0
                    minutes.value++
                    if (minutes.value === 60) {
                        minutes.value = 0
                        hours.value++
                    }
                }
            }, 1000)
        }

        const pauseTimer = () => {
            recording.value = true
            paused.value = true
            clearInterval(timer) 
        }

        const stopTimer = () => {
            recording.value = false
            paused.value = false

            emit('addTask', {
                id: Math.floor(Math.random() * 1000),
                icon: `${Math.floor(Math.random() * 2) == 0 ? 'loom' : 'evernote'}`,
                title: 'Recording',
                time: `${hours.value < 10 ? '0'+hours.value : hours.value}:${minutes.value < 10 ? '0'+minutes.value : minutes.value}:${seconds.value < 10 ? '0'+seconds.value : seconds.value}`,
            })

            clearInterval(timer)
            seconds.value = 0
            minutes.value = 0
            hours.value = 0
        }

        const handleHistory = () => {
            console.log('Accessed the history.')
        }

        return {
            recording,
            paused,
            loadTasks,
            timer,
            seconds,
            minutes,
            hours,
            startTimer,
            stopTimer,
            pauseTimer,
            handleHistory,
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
    width: 340px;
    height: 40px;
    margin-bottom: 5px;
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