<template>
  <div class="apps-container">
    <Sidebar
      :currentUser="currentUser"
      :isOpen="isSidebarOpen"
      :class="{ closed: !isSidebarOpen }"
    />
    <Header
      :currentUser="currentUser"
      :isSidebarOpen="isSidebarOpen"
    />
    <div class="components" :style="!isSidebarOpen ? 'margin-left: 100px;' : ''">
      <div class="inner-components">
        <TimeTracker :previousTasks="previousTasks" @addTask="addTask" />
        <div class="small-components">
          <DailyHours :dailyHours="dailyHours" />
          <CoursesProgress :currentCourse="currentCourse" />
        </div>
        <Collaborators
          :currentUser="currentUser"
          :collab="collab"
          :collabComments="collabComments"
          @handleLike="handleLike"
          @addComment="addComment"
        />
      </div>
      <div class="inner-components">
        <CoursesGeneral :teachers="teachers" />
        <Feedback />
      </div>
    </div>
  </div>
</template>

<script>
import Sidebar from "@/components/Sidebar.vue"
import Header from "@/components/Header.vue"
import TimeTracker from "@/components/TimeTracker.vue"
import DailyHours from "@/components/DailyHours.vue"
import CoursesProgress from "@/components/CoursesProgress.vue"
import Collaborators from "@/components/Collaborators.vue"
import CoursesGeneral from "@/components/CoursesGeneral.vue"
import Feedback from "@/components/Feedback.vue"
import { ref, watch } from "vue"

export default {
  name: "index",
  components: {
    Header,
    TimeTracker,
    DailyHours,
    CoursesProgress,
    Collaborators,
    CoursesGeneral,
    Feedback,
    Sidebar,
  },
  props: {},
  setup() {
    let currentUser = ref({
      name: "Sophia Williams",
      email: "sophia@gmail.com",
      gender: "F",
    })

    let collab = ref({
      name: "Matthew Johson",
      position: "Software Engineer",
      description: "Employee of the month!",
    })

    let collabComments = ref([
      {
        user: "James Brown",
        comment: "Congrats, Matthew! 🔥",
        liked: true,
      },
      {
        user: "Lena Müller",
        comment: "Great work! 🤗",
        liked: true,
      },
      {
        user: "Juma Omondi",
        comment: "The sky is the limit! ⚡️",
        liked: false,
      },
    ])

    const handleLike = (index) => {
      collabComments.value[index].liked = !collabComments.value[index].liked
    }

    let currentCourse = ref({
      title: "Team Diversity",
      subtitle: "Designed to promote inclusivity and diverse perspectives.",
    })

    let teachers = ref([
      {
        name: "Nuray Aksoy",
        position: "Product Manager",
        course: "Time Management",
        date: "Aug 21 - Sep 04",
        progress: "30%",
        status: "In progress",
      },
      {
        name: "Arthur Taylor",
        position: "CEO",
        course: "Leadership Skills",
        date: "Ago 02 - Ago 18",
        progress: "70%",
        status: "In progress",
      },
      {
        name: "Lena Müller",
        position: "Marketing Manager",
        course: "Diversity Training",
        date: "Jun 24 - Jul 03",
        progress: "100%",
        status: "Completed",
      },
      {
        name: "Wei Chen",
        position: "Operations Manager",
        course: "Efficiency at Work",
        date: "Jun 04 - Jul 28",
        progress: "100%",
        status: "Completed",
      },
    ])

    let dailyHours = ref({
      hours: 12,
      minutes: 27,
    })

    let previousTasks = ref([
      {
        icon: "loom",
        title: "Meeting - Commercial",
        time: "1:23:05",
      },
      {
        icon: "evernote",
        title: "Dashboard - Redesign",
        time: "3:14:26",
      },
    ])

    const addTask = (task) => {
      previousTasks.value.unshift(task)
    }

    const addComment = (comment) => {
      collabComments.value.unshift(comment)
    }

    const isSidebarOpen = ref(true)

    const toggleSidebar = () => {
      isSidebarOpen.value = !isSidebarOpen.value
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
      isSidebarOpen,
      toggleSidebar,
    }
  },
}
</script>

<style lang="scss" scoped>
@use "assets/scss/main";

.apps-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  width: 100%;
  min-width: 850px;
  position: relative;
  overflow: hidden;
}

.components {
  flex: 1;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-wrap: wrap;
  gap: 24px;
  padding: calc(83px + 2rem) 1rem 2rem; 
  margin-left: 100px;
  overflow-y: auto;

  &::-webkit-scrollbar {
    width: 8px;
  }

  &::-webkit-scrollbar-track {
    background: transparent;
  }

  &::-webkit-scrollbar-thumb {
    background-color: rgba(0, 0, 0, 0.2);
    border-radius: 4px;
  }
}

.small-components {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 412px;
  width: 352px;
  min-width: 280px;
  max-width: 100%;
}

.inner-components {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  gap: 24px;
  width: 100%;
  max-width: 1200px;
  flex-wrap: wrap;
  margin: 0 auto;
}

</style>
