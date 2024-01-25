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
            <Feedback />
        </div>
    </div>
</template>

<script>


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