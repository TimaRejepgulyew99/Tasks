<template>
  <div class>
    <div class="text-muted">
      <div class="row mb-3">
        <div class="col-12 bg-white shadow-sm pt-2 pb-2 mr-auto">
          <label class="mr-sm-2 col-12" for="inlineFormCustomSelect">Искать по тэгу</label>
          <div class="form-group d-flex col-6">
            <input type="text" class="form-control" />
            <input value="искать" class="btn btn-dark" type="button" />
            <router-link class="btn btn-outline-success col-6 ml-auto " to="/create-tasks">
              <a class>Создать задачу</a>
            </router-link>
          </div>
        </div>
      </div>
      <div class="row mt-2">
        <div class="col-1">
          <div class="d-block col-auto rounded pt-2 pb-2 m-3">#</div>
        </div>
        <div class="col-2">
          <div class="media-body m-4">
            <div class="d-block align-content-center text-gray-dark">Заголовок</div>
          </div>
        </div>
        <div class="col-3">
          <div class="media-body m-4">
            <div class="d-block align-content-center text-gray-dark">Описание</div>
          </div>
        </div>
        <div class="col-2">
          <div class="media-body m-4">
            <div class="d-block align-content-center text-gray-dark">статус</div>
          </div>
        </div>
        <div class="col-4">
          <router-link class="btn btn-outline-success m-4" to="/create-tasks">
            <a class>Создать задачу</a>
          </router-link>
        </div>
      </div>

      <div class="bg-white mb-3 shadow-sm row" v-for="(task, index) in tasks" :key="index">
        <div class="col-1">
          <div class="d-block col-auto rounded pt-2 pb-2 m-3">{{ index+1}}</div>
        </div>

        <div class="col-2">
          <div class="d-block short-form col-auto rounded pt-2 pb-2 m-3">{{ task.header }}</div>
        </div>
        <div class="col-3">
          <div class="d-block short-form col-auto rounded pt-2 pb-2 m-3">{{ task.description }}</div>
        </div>

        <div class="col-2">
          <div class="d-block col-auto rounded pt-2 pb-2 m-3">{{ task.deadLineTask }}</div>
        </div>
        <div class="col-4">
          <router-link :to="{name:'more-about',params:{taskId:task.id}}">
            <a class="btn btn-outline-success m-4">Подробнее</a>
          </router-link>
        </div>
      </div>
      <slot></slot>
    </div>
  </div>
</template>
<script>
import auxios from 'axios'
export default {
  mounted(){
     auxios
      .get('https://192.168.4.99:32772/api/task')
      .then(response => (this.tasks = response.data))
      .then(response=>(console.log(response[0])));
  },
  data() {
    return {
      filterTag: "null",
      filterTasks: this.$store.getters.tasks,
      id: "",
      tasks: null
    };
  },
  watch: {
    filterTag: function(val) {
      if (val != "null") {
        this.filterTasks = this.tasks.filter(task => {
          for (let tag in task.tags) {
            if (task.tags[tag] == val) {
              return task;
            }
          }
        });
      } else {
        this.filterTasks = this.tasks;
      }
    }
  }
};
</script>
<style lang="css">
.bg--purple {
  background: #f4f6fc;
}
</style>
