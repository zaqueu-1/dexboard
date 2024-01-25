<template>
    <div class="apps-container">
        <TimeTracker />
        <div>
            <DailyHours />
            <CoursesProgress />
        </div>
    </div>
</template>

<script>

</script>

<style lang="scss" scoped>
@use 'assets/scss/main';

.apps-container {
    background-color: white;
    padding: 20px;
    text-align: center;
    height: calc(100% - 88px);
    width: calc(100% - 340px);
    padding: 0 32px;
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
    justify-self: flex-end;
    position: fixed;
    bottom: 0;
    right: 0;
}
</style>