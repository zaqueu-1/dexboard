# Dexboard - Modern Dashboard

![Vue.js](https://img.shields.io/badge/vuejs-%2335495e.svg?style=for-the-badge&logo=vuedotjs&logoColor=%234FC08D) ![Nuxtjs](https://img.shields.io/badge/Nuxt-002E3B?style=for-the-badge&logo=nuxtdotjs&logoColor=#00DC82) ![SASS](https://img.shields.io/badge/SASS-hotpink.svg?style=for-the-badge&logo=SASS&logoColor=white)

A modern and responsive dashboard interface built with Vue 3 and SCSS. Originally started as a frontend challenge, it evolved into a portfolio project showcasing modern web development practices and UI/UX design principles.

## 🌐 Live Demo

[View Demo](https://frontend-case-nu.vercel.app/)

## 🚀 Features

### Interactive Components

- **Time Tracker**: Functional stopwatch with stop, pause, resume, and start options. Recordings are saved and displayed at the top of 'Previous Tasks'
- **Daily Hours**: Visual representation of daily activity
- **Course Progress**: Track learning progress with interactive elements
- **Team Collaboration**: Like/unlike comments and add new comments as the current user
- **Course Management**: Search courses by name and view all courses
- **Daily Feedback**: Choose mood and add comments

## 🛠️ Tech Stack

- Vue 3 (Composition API)
- Nuxt.js
- SCSS/SASS
- JavaScript (ES6+)
- Modern CSS Features
- Responsive Design

## 🏃‍♂️ Getting Started

### Prerequisites

- Node.js (v14.0.0 or higher)
- npm or yarn

### Installation

1. Clone the repository

```bash
git clone https://github.com/zaqueu-1/dexboard.git
cd dexboard
```

2. Install dependencies

```bash
npm install
# or
yarn install
```

3. Start the development server

```bash
npm run dev
# or
yarn dev
```

Then open http://localhost:3000 in your browser.

## 📁 Project Structure

```
dexboard/
├── components/
│   ├── icons/        # SVG icons components
│   ├── emojis/       # Emoji components
│   └── ...           # Main components
├── assets/
│   └── scss/         # SCSS styles
├── pages/            # Vue pages
└── public/           # Static assets
```

### Component Architecture

- Components are properly isolated and receive props from the index
- SVG elements are componentized for better code readability
- Dynamic loading of components
- Interactive features in each component

## 🎨 Key Components

- **TimeTracker**:
  - Functional stopwatch
  - Task recording and history
- **DailyHours**:
  - Activity visualization
  - Details view
- **CoursesProgress**:
  - Progress tracking
  - Interactive buttons
- **Collaborators**:
  - Comment system
  - Like/unlike functionality
- **CoursesGeneral**:
  - Course search
  - Course listing
- **Feedback**:
  - Mood selection
  - Comment submission

## 📝 Notes

This project was an exciting opportunity to work with Nuxt and SASS, offering a different experience from my usual stack (Vue + Quasar). The ease of development with just some documentation reading was impressive, making it a combination I look forward to using more in the future.
