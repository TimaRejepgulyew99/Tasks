<template>
<<<<<<< HEAD
  <div id="app" class="d-flex">
    <sidebar-menu class=" bg-white  " :menu="menu" />
    
    <main class="bg--purple col-9 p-0">
      <header class="d-flex align-items-center bg-white mb-5">
        <h5 class="mr-md-auto pl-5 pr-5 font-weight-normal text-center">
          Turkmen
          <br />tranzit
        </h5>
        <nav class="my-2 my-md-0 mr-md-3">
          <a class="p-2 text-dark" href="#">
            <router-link to="/">мои задачи</router-link>
          </a>
        </nav>
        <a class="btn btn-outline-primary" href="#">Sign up</a>
      </header>
      <div class="flex flex-wrap">
        <router-view class="bg--purple full-height m-5"></router-view>
      </div>
    </main>
=======
  <div class="container height-100" id="app">
    <div class="d-flex flex-md-row align-items-center p-3 mb-3 bg-white shadow-sm">
      <h5 class="my-0 mr-md-auto font-weight-normal">Turkmen tranzit</h5>
      <nav class="my-2 my-md-0 mr-md-3">
        <router-link class="p-2 text-dark" to="/">главная</router-link>
        <router-link class="p-2 text-dark" to="/news">новости</router-link>
      </nav>
      <router-link class="btn btn-outline-primary" to="/profile">Мой аккаунт</router-link>
    </div>

    <router-view class="height"></router-view>
    <footer class=" footer border shadow-sm p-3">
      <router-link class="p-2 text-dark" :to="'/'">главная</router-link><br>
      <router-link class="p-2 text-dark" to="/news">новости</router-link><br>
      <router-link class="p-2 text-dark" to="/profile">Мой аккаунт</router-link>
    </footer>
>>>>>>> 5aa46bcf954918e3e512cf54baf251f816ca3e37
  </div>
</template>

<script>
export default {
  name: "app",
<<<<<<< HEAD
  data() {
    return {
      menu: [
        {
          href: "/",
          title: "Меню",
          icon: "home"
        },
        {
          href: "/create-tasks",
          title: "Создать задачу",
          icon: "plus"
        }
      ]
    };
  }
=======
  computed: {}
>>>>>>> 5aa46bcf954918e3e512cf54baf251f816ca3e37
};
</script>

<style>

button{
  margin:  0 auto;
  display: block;

  background: lightblue;
  border: none;
   width: 2vw;
  height: 2vw;
  background: gray url(../img/menu--icon.jpg) no-repeat;
  background-size: 2vw 2vw;
  background-position: center
}
.home{
  display: inline-block;
position: relative;
  top: 0;
  left: 0;
  
  width: 2vw;
  height: 2vw;
  background: gray url(../img/menu--icon.jpg) no-repeat;
  background-size: 2vw 2vw;
  background-position: center
}
.plus:before{
  content: '+';
  font-size: 3vw;
}
a {
  color: black;
  text-decoration: none;
}
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
.bg--purple {
  background: #f4f6fc;
}
.fullHeight {
  height: 100%;
}
.short-form {
  text-overflow: ellipsis;
  overflow: hidden;
  width: 10vw;
  white-space: nowrap;
  
}
.height{
  min-height:74vh;
}
.full-height {
  height: 100vw;
}
</style>
