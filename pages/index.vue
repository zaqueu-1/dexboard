<template>
    <div class="apps-main">
        <Sidebar />
        <Header />
        <div class="apps-container">
            <TimeTracker />
            <div class="small-components">
                <DailyHours :dailyHours="dailyHours"/>
                <CoursesProgress :currentCourse="currentCourse" />
            </div>
            <Collaborators :collab="collab" :collabComments="collabComments" @handleLike="handleLike" />
            <CoursesGeneral :teachers="teachers" />
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

        let teachers = ref([
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

        let dailyHours = ref({
            hours: 12,
            minutes: 27,
        })

        return {
            collab,
            collabComments,
            handleLike,
            currentCourse,
            teachers,
            dailyHours,
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