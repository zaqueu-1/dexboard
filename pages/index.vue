<template>
    <div class="apps-container">
        <Sidebar :currentUser="currentUser" />
        <div class="components">
            <Header :currentUser="currentUser" />
            <div class="inner-components">
                <TimeTracker :previousTasks="previousTasks" @addTask="addTask" />
                <div class="small-components">
                    <DailyHours :dailyHours="dailyHours"/>
                    <CoursesProgress :currentCourse="currentCourse" />
                </div>
                <Collaborators :currentUser="currentUser" :collab="collab" :collabComments="collabComments" @handleLike="handleLike" @addComment="addComment" />
            </div>
            <div class="inner-components">
                <CoursesGeneral :teachers="teachers" />
                <Feedback />
            </div>
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
        let currentUser = ref({
            name: 'Sophia Williams',
            email: 'sophia@jurisoft.com',
            gender: 'F',
        })

        let collab = ref({
            name: 'Matthew Johson',
            position: 'Engenheiro de Software',
            description: 'Funcionário de melhor desempenho de dezembro!'
        })

        let collabComments = ref([
            {
                user: 'James Brown',
                comment: 'Parabéns, Matthew! 🔥', 
                liked: true,
            },
            {
                user: 'Lena Müller',
                comment: 'Ótimo trabalho! 🤗',
                liked: true,
            },
            {
                user: 'Juma Omondi',
                comment: 'O céu é o limite! ⚡️',
                liked: false,
            },
        ])

        const handleLike = (index) => {
            collabComments.value[index].liked = !collabComments.value[index].liked
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

        let previousTasks = ref([
            {
                icon: 'loom',
                title: 'Alinhamento - Comercial',
                time: '1:23:05'
            },
            {
                icon: 'evernote',
                title: 'Dashboard - Redesign',
                time: '3:14:26'
            },
        ])

        const addTask = (task) => {
            previousTasks.value.unshift(task)
        }

        const addComment = (comment) => {
            collabComments.value.unshift(comment)
        }

        return {
            currentUser,
            collab,
            collabComments,
            handleLike,
            currentCourse,
            teachers,
            dailyHours,
            previousTasks,
            addTask,
            addComment,
        }
    },
}
</script>

<style lang="scss" scoped>
@use 'assets/scss/main';

.apps-container {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    overflow: hidden;
}

.small-components {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;
    height: 412px;
    width: 352px ;
}

.components {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-wrap:wrap;
    gap: 24px;
    padding: 0 2rem 4rem 2rem;
    min-width: 400px;
    overflow-y: scroll;
    height: calc(100% - 4rem);
    scroll-behavior: smooth;
    width: 100%;
}

.inner-components {
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
    gap: 24px;
    width: 100%;
}
</style>