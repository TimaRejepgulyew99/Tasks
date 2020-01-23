<template>
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
  </div>
</template>

<script>
export default {
  name: "app",
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
.full-height {
  height: 100vw;
}
</style>
