<template>
    <div class="apps-main">
        <Sidebar />
        <Header />
        <div class="apps-container">
            <TimeTracker />
            <div class="small-components">
                <DailyHours />
                <CoursesProgress :currentCourse="currentCourse" />
            </div>
            <Collaborators :collab="collab" :collabComments="collabComments" @handleLike="handleLike" />
            <CoursesGeneral />
            <Feedback />
        </div>
    </div>
</template>

<script>
import Sidebar from '@/components/Sidebar.vue'
import Header from '@/components/Header.vue'
import TimeTracker from '@/components/TimeTracker.vue'
import DailyHours from '@/components/DailyHours.vue'
import CoursesProgress from '@/components/CoursesProgress.vue'
import Collaborators from '@/components/Collaborators.vue'
import CoursesGeneral from '@/components/CoursesGeneral.vue'
import Feedback from '@/components/Feedback.vue'
import { ref } from 'vue'

export default {
    name: 'index',
    components: {
    Header,
    TimeTracker,
    DailyHours,
    CoursesProgress,
    Collaborators,
    CoursesGeneral,
    Feedback,
    Sidebar
},
    props: {

    },
    setup() {
        let collab = ref({
            name: 'Matthew Johson',
            position: 'Engenheiro de Software',
            description: 'Funcionário de melhor desempenho de dezembro!'
        })

        let collabComments = ref({
            users: ['James Brown', 'Lena Müller', 'Juma Omondi'],
            comments: ['Parabéns, Matthew! 🔥', 'Ótimo trabalho! 🤗', 'O céu é o limite! ⚡️'],
            liked: [true, true, false]
        })

        const handleLike = (index) => {
            collabComments.value.liked[index] = !collabComments.value.liked[index]
        }

        let currentCourse = ref({
            title: 'Diversidade da equipe',
            subtitle: 'Projetado para promover a inclusividade e perspectivas diversas.',
        })

        return {
            collab,
            collabComments,
            handleLike,
            currentCourse,
        }
    },
}
</script>

<style lang="scss" scoped>
@use 'assets/scss/main';

.apss-main {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    justify-content: flex-start;
    width: calc(100% - 340px);
    min-height: 100vh;
    overflow-y: scroll;
    position: relative;
}

.apps-container {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    gap: 16px;
    padding: .5rem 0;
    flex-wrap: wrap;
    width: calc(100% - 272px);
    position: absolute;
    top: 88px;
    right: 0;
    min-height: 100vh;
    overflow-y: scroll;
    padding-bottom: 2rem;
}

.small-components {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    height: 412px;
}
</style>