<template>
    <div class="collabs-container">
        <div class="collabs-header">
            <div class="collabs-header-title">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M12 1.65002L15.8034 7.21472L22.2717 9.11282L18.1542 14.4498L18.3477 21.1872L12 18.921L5.65227 21.1872L5.84577 14.4498L1.72827 9.11282L8.19657 7.21472L12 1.65002ZM12 4.83962L9.31977 8.76183L4.76127 10.0983L7.66377 13.8585L7.52607 18.606L12 17.0094L16.473 18.606L16.3362 13.8585L19.2378 10.0983L14.6802 8.76183L12 4.83962ZM10.2 12C10.2 12.4774 10.3896 12.9353 10.7272 13.2728C11.0647 13.6104 11.5226 13.8 12 13.8C12.4774 13.8 12.9352 13.6104 13.2728 13.2728C13.6103 12.9353 13.8 12.4774 13.8 12H15.6C15.6 12.9548 15.2207 13.8705 14.5456 14.5456C13.8704 15.2207 12.9548 15.6 12 15.6C11.0452 15.6 10.1295 15.2207 9.45439 14.5456C8.77926 13.8705 8.39997 12.9548 8.39997 12H10.2Z" fill="#525866"/>
                </svg>
                <p>Destaque colaboradores</p>
            </div>
            <div v-if="option != ''" class="send-btn">
                <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M10.75 11.5H9.25C8.0197 11.4995 6.81267 11.8354 5.75941 12.4712C4.70614 13.107 3.8467 14.0186 3.274 15.1075C3.2579 14.9054 3.2499 14.7027 3.25 14.5C3.25 10.3577 6.60775 7 10.75 7V2.875L18.625 9.25L10.75 15.625V11.5ZM9.25 10H12.25V12.481L16.2408 9.25L12.25 6.019V8.5H10.75C9.88769 8.49903 9.03535 8.68436 8.25129 9.04332C7.46724 9.40227 6.76999 9.92637 6.20725 10.5798C7.17574 10.1959 8.20822 9.99919 9.25 10Z" fill="#525866"/>
                </svg>
                <p>Enviar</p>
            </div>
        </div>
        <div class="collab-app">
            <div class="collab-app-header">
                <p @click="handleOption('geral')" :style="option == 'geral' ? 'height:28px;background:white;padding:0 2px;color:#0A0D14' : ''">Geral</p>
                <p @click="handleOption('comentários')" :style="option == 'comentários' ? 'height:28px;background:white;padding:0 2px;color:#0A0D14' : ''">Comentários</p>
                <p @click="handleOption('prêmios')" :style="option == 'prêmios' ? 'height:28px;background:white;padding:0 2px;color:#0A0D14' : ''">Prêmios</p>
            </div>
            <div v-if="option == 'geral'" class="collab-app-body-general">
                <p>{{ collab.name }}</p>
                <p>{{ collab.position }}</p>
                <IconCollabsUser />
                <p>{{  collab.description }}</p>
            </div>
            <div v-if="option == 'comentários'" class="collab-app-body-comments">
                <div class="comment">
                    <IconUserJames />
                    <div>
                        <p>{{ collabComments.users[0] }}</p>
                        <p>{{ collabComments.comments[0] }}</p>
                    </div>
                    <span @click="$emit(`handleLike`,0)">
                        <IconHeartFull v-if="collabComments.liked[0] == true"/>
                        <IconHeartEmpty v-else/>
                    </span>
                </div>
                <div class="divider"></div>
                <div class="comment">
                    <IconUserLena />
                    <div>
                        <p>{{ collabComments.users[1] }}</p>
                        <p>{{ collabComments.comments[1] }}</p>
                    </div>
                    <span @click="$emit(`handleLike`,1)">
                        <IconHeartFull v-if="collabComments.liked[1] == true"/>
                        <IconHeartEmpty v-else/>
                    </span>
                </div>
                <div class="divider"></div>
                <div class="comment">
                    <IconUserJuma />
                    <div>
                        <p>{{ collabComments.users[2] }}</p>
                        <p>{{ collabComments.comments[2] }}</p>
                    </div>
                    <span @click="$emit(`handleLike`,2)">
                        <IconHeartFull v-if="collabComments.liked[2] == true"/>
                        <IconHeartEmpty v-else/>
                    </span>
                </div>
                <div class="comment-btn">
                    <svg width="21" height="20" viewBox="0 0 21 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M13.296 8.26456L12.2355 7.20406L5.25 14.1896V15.2501H6.3105L13.296 8.26456ZM14.3565 7.20406L15.417 6.14356L14.3565 5.08306L13.296 6.14356L14.3565 7.20406ZM6.9315 16.7501H3.75V13.5678L13.8263 3.49156C13.9669 3.35096 14.1576 3.27197 14.3565 3.27197C14.5554 3.27197 14.7461 3.35096 14.8868 3.49156L17.0085 5.61331C17.1491 5.75396 17.2281 5.94469 17.2281 6.14356C17.2281 6.34244 17.1491 6.53317 17.0085 6.67381L6.93225 16.7501H6.9315Z" fill="#525866"/>
                    </svg>
                    <span>Comment</span>
                </div>
            </div>
            <div v-if="option == 'prêmios'" class="collab-app-body-general">
                <p>Cartão presente de R$ 50,00</p>
                <p>Aproveite o prêmio, {{ collab.name.slice(0,7) }}!</p>
                <IconPrizes />
                <p>Os funcionários do mês recebem recompensas</p>
            </div>
            <div v-if="option == ''" class="collab-app-no-body">
                <IconNoCollabs />
                <p>Sem registros do destaque do funcionário ainda. Por favor, verifique mais tarde.</p>
            </div>
        </div>
    </div>
</template>

<script>
import IconNoCollabs from './icons/IconNoCollabs.vue'
import IconCollabsUser from './icons/IconCollabsUser.vue'
import IconPrizes from './icons/IconPrizes.vue'
import IconUserJames from './icons/IconUserJames.vue'
import IconUserJuma from './icons/IconUserJuma.vue'
import IconUserLena from './icons/IconUserLena.vue'
import IconHeartFull from './icons/IconHeartFull.vue'
import IconHeartEmpty from './icons/IconHeartEmpty.vue'
import { ref } from 'vue'

export default {
    name: 'Collaborators',
    components: {
    IconNoCollabs,
    IconCollabsUser,
    IconPrizes,
    IconUserJames,
    IconUserJuma,
    IconUserLena,
    IconHeartFull,
    IconHeartEmpty,
    IconHeartFull
},
    props: {
        collab: {
            type: Object,
        },
        collabComments: {
            type: Object,
        }
    },
    setup(props) {
        let option = ref('')

        onMounted(() => {
            props.collab && props.collabComments ? option.value = 'geral' : option.value = ''
        })

        const handleOption = (type) => {
            option.value = type
        }

        return {
            option,
            handleOption,
        }
    },
}
</script>

<style lang="scss" scoped>
@use 'assets/scss/main';

.collabs-container {
    @include main.tall-container();
}

.collabs-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 320px;
    margin-top: -.75rem;
    p {
        @include main.text-header();
        color: main.$text-main-900;
    }
    .send-btn {
        display: flex;
        align-items: center;
        justify-content: center;
        gap: .5rem;
        height: 32px;
        width: 85px;
        border-radius: 8px;
        border: 1px solid main.$soft-200;
        background-color: white;
        cursor: pointer;
        p {
            @include main.text-main();
            color: main.$text-sub-500;
        }
    }

    .collabs-header-title {
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

.collab-app {
    margin-top: .75rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
}
.collab-app-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: .5rem;
    width: 320px;
    height: 36px;
    background-color: main.$bg-weak-100;
    padding: 0 4px;
    border-radius: 10px;
    & > p {
        @include main.text-main();
        color: main.$soft-400;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 101.3px;
        height: 36px;
        padding: 4px 2px;
        border-radius: 6px;
        cursor: pointer;
    }
}
.collab-app-body-general {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 16px;
    height: 300px;
    width: 320px;
    p:first-of-type{
        @include main.text-header();
        color: main.$text-main-900;
        font-size: 18px;
    }
    p:nth-of-type(2) {
        @include main.text-sub();
        color: main.$text-sub-500;
        margin-top: -.75rem;
    }
    p:nth-of-type(3) {
        @include main.text-sub();
        color: main.$text-sub-500;
        margin-top: 1.25rem;
    }
    svg {
        margin-top: .75rem;
    }
}

.collab-app-body-comments {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 16px;
    height: 300px;
    width: 320px;
    margin-top: .5rem;
    p {
        @include main.text-main();
        color: main.$soft-400;
        font-size: 11px;
        line-height: 12px;
        letter-spacing: 2%;
    }
}

.collab-app-no-body {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0 16px;
    height: 300px;
    width: 320px;
    p{
        @include main.text-header-sub();
        color: main.$soft-400;
        text-align: center;
        margin-top: 2.5rem;
        height: 40px;
    }
    svg {
        margin: 1.5rem 0 .5rem 0;
    }
}

.comment {
    width: 320px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: .5rem 0;
    & > div {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        width: 236px;
        & > p:nth-child(1) {
            @include main.text-sub();
            color: main.$text-sub-500;
        }
        & > p:nth-child(2) {
            margin-top: -.35rem;
            @include main.text-header-sub();
            color: main.$text-main-900;
        }
    }
}

.comment-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    width: 320px;
    height: 36px;
    border: 1px solid main.$soft-200;
    border-radius: 8px;
    padding: 0 8px;
    margin-top: 1.25rem;
    cursor: pointer;
    span {
        @include main.text-main();
        color: main.$text-sub-500;
    }
}

.divider {
    @include main.divider();
    margin: .75rem 0;
}
</style>