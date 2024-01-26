<template>
    <div class="feedback-container">
        <div class="feedback-header">
            <div class="feedback-header-title">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M13.8 21.45L11.28 18.3H6.60001C6.36131 18.3 6.13239 18.2052 5.96361 18.0364C5.79483 17.8676 5.70001 17.6387 5.70001 17.4V7.5927C5.70001 7.35401 5.79483 7.12509 5.96361 6.9563C6.13239 6.78752 6.36131 6.6927 6.60001 6.6927H21C21.2387 6.6927 21.4676 6.78752 21.6364 6.9563C21.8052 7.12509 21.9 7.35401 21.9 7.5927V17.4C21.9 17.6387 21.8052 17.8676 21.6364 18.0364C21.4676 18.2052 21.2387 18.3 21 18.3H16.32L13.8 21.45ZM15.4551 16.5H20.1V8.4927H7.50001V16.5H12.1449L13.8 18.5682L15.4551 16.5ZM3.00001 3H18.3V4.8H3.90001V14.7H2.10001V3.9C2.10001 3.66131 2.19483 3.43239 2.36361 3.2636C2.53239 3.09482 2.76131 3 3.00001 3Z" fill="#525866"/>
                </svg>
                <p>Feedback diário</p>
            </div>
        </div>
        <div class="feedback-app">
            <div class="divider"></div>
            <div v-if="!showFeedbacks" class="feedback-app-body">
                <svg width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                <rect width="40" height="40" rx="20" fill="#FEF3EB"/>
                <path d="M20 29C15.0293 29 11 24.9707 11 20C11 15.0293 15.0293 11 20 11C24.9707 11 29 15.0293 29 20C29 24.9707 24.9707 29 20 29ZM20 27.2C21.9096 27.2 23.7409 26.4414 25.0912 25.0912C26.4414 23.7409 27.2 21.9096 27.2 20C27.2 18.0904 26.4414 16.2591 25.0912 14.9088C23.7409 13.5586 21.9096 12.8 20 12.8C18.0904 12.8 16.2591 13.5586 14.9088 14.9088C13.5586 16.2591 12.8 18.0904 12.8 20C12.8 21.9096 13.5586 23.7409 14.9088 25.0912C16.2591 26.4414 18.0904 27.2 20 27.2ZM15.5 20H17.3C17.3 20.7161 17.5845 21.4028 18.0908 21.9092C18.5972 22.4155 19.2839 22.7 20 22.7C20.7161 22.7 21.4028 22.4155 21.9092 21.9092C22.4155 21.4028 22.7 20.7161 22.7 20H24.5C24.5 21.1935 24.0259 22.3381 23.182 23.182C22.3381 24.0259 21.1935 24.5 20 24.5C18.8065 24.5 17.6619 24.0259 16.818 23.182C15.9741 22.3381 15.5 21.1935 15.5 20Z" fill="#FF4A00"/>
                </svg>
                <p>Como você classificaria seu humor hoje?</p>
                <p>Compartilhe seu humor para nos ajudar a entender.</p>
                <div class="emojis">
                    <span @click="handleMood(1)" :class="mood.mood == 1 ? 'selected' : ''">
                        <EmojiSad />
                    </span>
                    <span @click="handleMood(2)" :class="mood.mood == 2 ? 'selected' : ''">
                        <EmojiNotSatisfied />
                    </span>
                    <span @click="handleMood(3)" :class="mood.mood == 3 ? 'selected' : ''">
                        <EmojiOk />
                    </span>
                    <span @click="handleMood(4)" :class="mood.mood == 4 ? 'selected' : ''">
                        <EmojiHappy />
                    </span>
                    <span @click="handleMood(5)" :class="mood.mood == 5 ? 'selected' : ''">
                        <EmojiRadiant />
                    </span>
                </div>
                <textarea name="mood" id="mood" v-model="mood.comment" cols="30" rows="10" placeholder="Adicionar comentário..."></textarea>
                <button @click="handleFeedback" :disabled="mood.mood == 0" class="send-btn">
                    <span>Enviar</span>
                </button>
            </div>
            <div v-else class="feedback-app-no-body">
                <IconNoFeedbacks />
                <p>Sem registros de feedback ainda. Por favor, verifique mais tarde.</p>
            </div>
        </div>
    </div>
</template>

<script>
import EmojiSad from './emojis/EmojiSad.vue'
import EmojiNotSatisfied from './emojis/EmojiNotSatisfied.vue'
import EmojiOk from './emojis/EmojiOk.vue'
import EmojiHappy from './emojis/EmojiHappy.vue'
import EmojiRadiant from './emojis/EmojiRadiant.vue'
import IconNoFeedbacks from './icons/IconNoFeedbacks.vue'
import { ref } from 'vue'

export default {
    name: 'Feedback',
    components: {
    EmojiSad,
    EmojiNotSatisfied,
    EmojiOk,
    EmojiHappy,
    EmojiRadiant,
    IconNoFeedbacks,
},
    props: {

    },
    setup() {
        let showFeedbacks = ref(false)
        let mood = ref({
            mood: 0,
            comment: ''
        })

        const handleMood = (number) => {
            mood.value = { ...mood, mood: number}
        }

        const handleFeedback = () => {
            mood.mood == 0 ? null : showFeedbacks.value = !showFeedbacks.value
        }

        return {
            handleFeedback,
            showFeedbacks,
            handleMood,
            mood
        }
    },
}
</script>

<style lang="scss" scoped>
@use 'assets/scss/main';

.feedback-container {
    @include main.tall-container();
    max-height: 380px;
}

.feedback-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 320px;
    margin-top: -.75rem;
    p {
        @include main.text-header();
        color: main.$text-main-900;
    }
    .feedback-header-title {
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

.feedback-app {
    margin-top: .75rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
}
.feedback-app-body {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 16px;
    height: 340px;
    width: 320px;
    p:first-of-type{
        @include main.text-header();
        color: main.$text-main-900;
    }
    p:nth-of-type(2) {
        @include main.text-sub();
        color: main.$text-sub-500;
        margin-top: -.75rem;
    }
    svg {
        margin-top: 1rem;
    }
    textarea {
        width: 295px;
        padding: 12px;
        height: 84px;
        border: main.$border-component;
        border-radius: 0 0 12px 12px;
        outline: none
    }
}

.divider {
    @include main.divider();
    margin-top: -.5rem;
}

.emojis {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 320px;
    height: 36px;
    margin-top: .5rem;
    span {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 64px;
        height: 36px;
        border: main.$border-component;
        cursor: pointer;
        transition: all .2s ease-in-out;
    }
    span:first-of-type {
        border-radius: 12px 0 0 0;
    }
    span:last-of-type {
        border-radius: 0 12px 0 0;
    }
    svg {
        margin-bottom: .75rem;
    }
}

.selected {
    background-color: main.$soft-200;
}

.send-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    width: 320px;
    height: 36px;
    border: 1px solid main.$soft-200;
    border-radius: 8px;
    margin-top: 1rem;
    background-color: white;
    cursor: pointer;
    span {
        @include main.text-main();
        color: main.$text-sub-500;
    }
    &:disabled {
        cursor: not-allowed;
    }
}

.feedback-app-no-body {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0 16px;
    height: 320px;
    width: 320px;
    p{
        @include main.text-header-sub();
        color: main.$soft-400;
        text-align: center;
        margin-top: 1.5rem;
        height: 40px;
    }
    svg {
        margin-top: 2.25rem;
    }
}
</style>