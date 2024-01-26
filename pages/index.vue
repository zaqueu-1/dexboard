<template>
    <div class="apps-main">
        <Header />
        <div class="apps-container">
            <TimeTracker />
            <div class="small-components">
                <DailyHours />
                <CoursesProgress />
            </div>
            <Collaborators />
            <CoursesGeneral />
            <Feedback />
        </div>
    </div>
</template>

<script>
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
        Feedback
    },
    props: {

    },
    setup() {

        return {

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