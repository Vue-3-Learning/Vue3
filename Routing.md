- [SetUp](#SetUp)
  ## Setup
  - npm install --save vue-router (add @next after vue-router to install latest) the restart your development server
  - go to main.js where we create our app we can now register this router
  - ```
    import { createApp } from 'vue';
    import {createRouter,createWebHistory} from 'vue-router'
    import App from './App.vue';
    import TeamsList from './components/teams/TeamsList.vue';
    import UsersList from './components/users/UsersList.vue';
    const router = createRouter({
    history:createWebHistory() ,
    routes:[
        {path: '/teams', component : TeamsList},
        {path: '/users', component : UsersList},
    ]
    })
    const app = createApp(App)
    app.use(router)
    app.mount('#app'); ```
  
