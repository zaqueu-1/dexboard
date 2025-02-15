<template>
  <div class="header-container" :class="{ 'sidebar-closed': !isSidebarOpen }">
    <div class="header-user-stats">
      <IconAvatar v-if="currentUser.name == 'Sophia Williams'" />
      <div class="header-user-stats-texts">
        <p>{{ currentUser.name }}</p>
        <p>
          {{
            currentUser.gender == "F" ? "Welcome back 👋🏻" : "Welcome back 👋🏻"
          }}
        </p>
      </div>
    </div>
    <div class="header-buttons">
      <button class="toggle-sidebar">
        <svg
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M3 18H21V16H3V18ZM3 13H21V11H3V13ZM3 6V8H21V6H3Z"
            fill="#525866"
          />
        </svg>
      </button>
      <svg
        style="cursor: pointer"
        width="40"
        height="40"
        viewBox="0 0 40 40"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <rect width="40" height="40" rx="8" fill="white" />
        <path
          d="M19.25 12.5C22.976 12.5 26 15.524 26 19.25C26 22.976 22.976 26 19.25 26C15.524 26 12.5 22.976 12.5 19.25C12.5 15.524 15.524 12.5 19.25 12.5ZM19.25 24.5C22.1502 24.5 24.5 22.1502 24.5 19.25C24.5 16.349 22.1502 14 19.25 14C16.349 14 14 16.349 14 19.25C14 22.1502 16.349 24.5 19.25 24.5ZM25.6137 24.5532L27.7355 26.6742L26.6742 27.7355L24.5532 25.6137L25.6137 24.5532Z"
          fill="#525866"
        />
      </svg>
      <IconNotification style="cursor: pointer" />
      <div class="calendar">
        <svg
          width="20"
          height="20"
          viewBox="0 0 20 20"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M7.75 1.75V3.25H12.25V1.75H13.75V3.25H16.75C16.9489 3.25 17.1397 3.32902 17.2803 3.46967C17.421 3.61032 17.5 3.80109 17.5 4V16C17.5 16.1989 17.421 16.3897 17.2803 16.5303C17.1397 16.671 16.9489 16.75 16.75 16.75H3.25C3.05109 16.75 2.86032 16.671 2.71967 16.5303C2.57902 16.3897 2.5 16.1989 2.5 16V4C2.5 3.80109 2.57902 3.61032 2.71967 3.46967C2.86032 3.32902 3.05109 3.25 3.25 3.25H6.25V1.75H7.75ZM16 8.5H4V15.25H16V8.5ZM12.277 9.352L13.3375 10.4125L9.625 14.125L6.973 11.473L8.035 10.4125L9.62575 12.004L12.2778 9.352H12.277ZM6.25 4.75H4V7H16V4.75H13.75V5.5H12.25V4.75H7.75V5.5H6.25V4.75Z"
            fill="#525866"
          />
        </svg>
        <p>Calendar</p>
      </div>
      <div class="new-request">
        <svg
          width="20"
          height="20"
          viewBox="0 0 20 20"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M9.25 9.25V4.75H10.75V9.25H15.25V10.75H10.75V15.25H9.25V10.75H4.75V9.25H9.25Z"
            fill="white"
          />
        </svg>
        <p>New request</p>
      </div>
    </div>
  </div>
</template>

<script>
import IconNotification from "./icons/IconNotification.vue"
import IconAvatar from "./icons/IconAvatar.vue"

export default {
  name: "Header",
  components: {
    IconNotification,
    IconAvatar,
  },
  props: {
    currentUser: {
      type: Object,
      required: true,
    },
    isSidebarOpen: {
      type: Boolean,
      required: true,
    },
  }
}
</script>

<style lang="scss" scoped>
@use "assets/scss/main";

.header-container {
  background-color: white;
  text-align: center;
  height: 88px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: #fff;
  width: calc(100% - 280px);
  min-width: 650px;
  max-width: 1200px;
  margin-left: 100px;
}

.sidebar-container.closed ~ .header-container {
  width: 100%;
}

.header-user-stats {
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  gap: 1rem;
  width: auto;
  padding: 0 0.25rem;
  p {
    margin: 0;
    font-size: 14px;
    line-height: 16px;
    color: #525866;
  }
  p:first-child {
    @include main.text-header();
    color: main.$text-main-900;
  }
  p:last-child {
    @include main.text-header-sub();
    color: main.$text-sub-500;
  }
}

.header-user-stats-texts {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  gap: 0;
}

.header-buttons {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 0.5rem;
  margin-left: 1rem;
  position: relative;
}

.toggle-sidebar {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  border: none;
  border-radius: 8px;
  background: white;
  cursor: pointer;

  &:hover {
    background: #f5f5f5;
  }
}

.calendar {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
  padding: 0 0.75rem;
  border: 1px solid #e2e4e9;
  border-radius: 10px;
  width: auto;
  min-width: 40px;
  height: 40px;
  cursor: pointer;
  p {
    @include main.text-main();
    color: main.$text-sub-500;
  }
}

.new-request {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 4px;
  padding: 0 0.75rem;
  border: none;
  border-radius: 10px;
  width: auto;
  min-width: 40px;
  height: 40px;
  background-color: main.$color-primary-base;
  cursor: pointer;
  white-space: nowrap;
  p {
    @include main.text-main();
    color: white;
  }
}
</style>
