<template>
    <div class="courses-general-container">
        <div class="courses-general-header">
            <div class="courses-general-header-title">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M20.1 4.8H7.49999C7.0226 4.8 6.56477 4.98964 6.2272 5.32721C5.88964 5.66477 5.69999 6.12261 5.69999 6.6C5.69999 7.07739 5.88964 7.53523 6.2272 7.87279C6.56477 8.21036 7.0226 8.4 7.49999 8.4H20.1V20.1C20.1 20.3387 20.0052 20.5676 19.8364 20.7364C19.6676 20.9052 19.4387 21 19.2 21H7.49999C6.54521 21 5.62954 20.6207 4.95441 19.9456C4.27928 19.2705 3.89999 18.3548 3.89999 17.4V6.6C3.89999 5.64522 4.27928 4.72955 4.95441 4.05442C5.62954 3.37928 6.54521 3 7.49999 3H19.2C19.4387 3 19.6676 3.09482 19.8364 3.2636C20.0052 3.43239 20.1 3.66131 20.1 3.9V4.8ZM5.69999 17.4C5.69999 17.8774 5.88964 18.3352 6.2272 18.6728C6.56477 19.0104 7.0226 19.2 7.49999 19.2H18.3V10.2H7.49999C6.86804 10.201 6.24705 10.0349 5.69999 9.7185V17.4ZM19.2 7.5H7.49999C7.2613 7.5 7.03238 7.40518 6.8636 7.2364C6.69482 7.06761 6.59999 6.83869 6.59999 6.6C6.59999 6.3613 6.69482 6.13239 6.8636 5.9636C7.03238 5.79482 7.2613 5.7 7.49999 5.7H19.2V7.5Z" fill="#525866"/>
                </svg>
                <p>Cursos</p>
            </div>
            <div v-if="users" class="courses-general-input">
                <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M9.25 2.5C12.976 2.5 16 5.524 16 9.25C16 12.976 12.976 16 9.25 16C5.524 16 2.5 12.976 2.5 9.25C2.5 5.524 5.524 2.5 9.25 2.5ZM9.25 14.5C12.1502 14.5 14.5 12.1502 14.5 9.25C14.5 6.349 12.1502 4 9.25 4C6.349 4 4 6.349 4 9.25C4 12.1502 6.349 14.5 9.25 14.5ZM15.6137 14.5532L17.7355 16.6742L16.6742 17.7355L14.5532 15.6137L15.6137 14.5532Z" fill="#868C98"/>
                </svg>
                <input type="text" placeholder="Pesquisar cursos..." />
            </div>
            <button v-if="users" class="details-btn">
                <span>Ver todos</span>
            </button>
        </div>
        <div class="courses-general-app">
            <div :class="users ? 'courses-general-app-header' : 'courses-general-app-header disabled'">
                <p>Professor</p>
                <p>Nome do curso</p>
                <p>Progresso</p>
                <p>Status</p>
                <p></p>
            </div>
            <div v-if="users" class="courses-general-app-body" v-for="user in users" :key="user.id">
                <div>
                    <IconUserLena v-if="user.name == 'Lena Müller'" /> 
                    <IconUserNuray v-if="user.name == 'Nuray Aksoy'" /> 
                    <IconUserArthur v-if="user.name == 'Arthur Taylor'" />
                    <IconUserWei v-if="user.name == 'Wei Chen'" />
                    <div>
                        <p>{{ user.name }}</p>
                        <p>{{ user.position.length > 8 ? user.position.slice(0,14)+'...' : user.position }}</p>
                    </div>
                </div>
                <div>
                    <p>{{ user.course }}</p>
                    <p>{{ user.date }}</p>
                </div>
                <div>
                    <Icon30 v-if="user.progress == '30%'"/>
                    <Icon70 v-if="user.progress == '70%'"/>
                    <Icon100 v-if="user.progress == '100%'"/>
                </div>
                <div>
                    <IconConcluded v-if="user.status == 'Concluído'" />
                    <IconOngoing v-if="user.status == 'Em andamento'" />
                </div>
                <div>
                    <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M16.7959 15.9992L13.0834 12.2867L14.1439 11.2262L18.9169 15.9992L14.1439 20.7722L13.0834 19.7117L16.7959 15.9992Z" fill="#525866"/>
                    </svg>
                </div>
            </div>
            <div v-if="!users" class="courses-general-no-body">
                <IconNoCourses />
                <p>Não há registros de cursos ainda.</p> 
                <p>Por favor, verifique mais tarde.</p>
            </div>
        </div>
    </div>
</template>

<script>
import IconUserLena from './icons/IconUserLena.vue'
import IconUserNuray from './icons/IconUserNuray.vue'
import IconUserArthur from './icons/IconUserArthur.vue'
import IconUserWei from './icons/IconUserWei.vue'
import IconConcluded from './icons/IconConcluded.vue'
import IconOngoing from './icons/IconOngoing.vue'
import Icon30 from './icons/Icon30.vue'
import Icon70 from './icons/Icon70.vue'
import Icon100 from './icons/Icon100.vue'
import IconNoCourses from './icons/IconNoCourses.vue'
import { ref } from 'vue'


export default {
    name: 'CoursesGeneral',
    components: {
    IconUserLena,
    IconUserNuray,
    IconUserArthur,
    IconUserWei,
    IconConcluded,
    IconOngoing,
    Icon30,
    Icon70,
    Icon100,
    IconNoCourses,
},
    props: {

    },
    setup() {
        let user = ref([
            {
                name: 'Nuray Aksoy',
                position: 'Gerente de produto',
                course: 'Time Management',
                date: 'Ago 21 - Set 04',
                progress: '30%',
                status: 'Em andamento',
            },
            {
                name: 'Arthur Taylor',
                position: 'CEO',
                course: 'Leadership Skills',
                date: 'Ago 02 - Ago 18',
                progress: '70%',
                status: 'Em andamento',
            },
            {
                name: 'Lena Müller',
                position: 'Gerente de marketing',
                course: 'Diversity Training',
                date: 'Jun 24 - Jul 03',
                progress: '100%',
                status: 'Concluído',
            },
            {
                name: 'Wei Chen',
                position: 'Gerente de operações',
                course: 'Efficiency at Work',
                date: 'Jun 04 - Jul 28',
                progress: '100%',
                status: 'Concluído',
            },
        ])

        let users = ref(null)

        return {
            users,
        }
    },

}
</script>

<style lang="scss" scoped>
@use 'assets/scss/main';

.courses-general-container {
    @include main.wide-container();
}

.courses-general-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 696px;
    margin-top: 0;
    p {
        @include main.text-header();
        color: main.$text-main-900;
    }
    .details-btn {
        @include main.details-button();
    }

    .courses-general-header-title {
        display: flex;
        align-items: center;
        justify-content: flex-start;
        gap: .5rem;
        width: 294px;
        height: 32px;
        p {
            @include main.text-header();
            color: main.$text-main-900;
        }
    }
}

.courses-general-input {
    width: 294px;
    height: 32px;
    border: 1px solid main.$soft-200;
    padding: 0 6px;
    border-radius: 8px;
    position: relative;
    svg {
        margin-top: .25rem;
        position: absolute;
        left: 8px;
        top: 2px;
    }
    input {
        @include main.text-main();
        color: main.$text-sub-500;
        width: 80%;
        height: 100%;
        border: none;
        outline: none;
        background-color: transparent;
        position: absolute;
        left: 32px;
    }
    input::placeholder {
        @include main.text-main();
        font-weight: 400;
        color: main.$soft-400;
    }
}

.courses-general-app {
    margin-top: 1rem;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
}
.courses-general-app-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: .5rem;
    width: 696px;
    height: 36px;
    background-color: main.$bg-weak-100;
    color: main.$text-sub-500;
    padding: 0 4px;
    border-radius: 8px;
    & > p {
        @include main.text-main();
        font-weight: 400;
        display: flex;
        align-items: center;
        justify-content: flex-start;
        height: 36px;
        padding: 4px 12px;
        cursor: pointer;
    }
    p:first-of-type{
        width: 208px;
    }
    p:nth-of-type(2) {
        width: 164px;
    }
    p:nth-of-type(3) {
        width: 140px;
    }
    p:nth-of-type(4) {
        width: 120px;
    }
    p:last-of-type {
        width: 64px;
    }
}

.disabled {
    color: main.$text-disabled-300; 
    cursor: not-allowed;
}
.courses-general-app-body {
    display: flex;
    align-items: center;
    height: 64px;
    width: 696px;
    padding: 3px 0;
    & > div {
        height: 64px;

    }
    div:first-child{
        width: 186px;
        display: flex;
        align-items: center;
        justify-content: center;
        div {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            justify-content: center;
            width: 102px;
            margin-left: .5rem;
            p:first-child {
                @include main.text-main();
                color: main.$text-main-900;
                font-weight: 400;
                margin-bottom: -.5rem;
            }
            p:last-child {
                @include main.text-soft();
                color: main.$text-sub-500;
                font-weight: 400;
            } 
        }
    }
    div:nth-child(2) {
        width: 164px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        p:first-child {
            @include main.text-main();
            color: main.$text-main-900;
            font-weight: 400;
            margin-bottom: -.5rem;
        }
        p:last-child {
            @include main.text-soft();
            color: main.$text-sub-500;
            font-weight: 400;
        }
    }
    div:nth-child(3) {
        width: 140px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }
    div:nth-child(4) {
        width: 142px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }
    div:last-child {
        width: 64px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }
}

.courses-general-no-body {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 0 16px;
    height: 300px;
    width: 320px;
    p:first-of-type, p:last-of-type {
        @include main.text-header-sub();
        color: main.$soft-400;
        text-align: center;
        height: 40px;
    }
    p:last-of-type {
        margin-top: -2rem;
    }
    svg {
        margin: 2.5rem 0 .5rem 0;
    }
}

</style>