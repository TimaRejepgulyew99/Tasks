<template>
  <div class="container">
    <div class="form d-flex flex-column" v-on:submit="makeTask()">
      <h1>Постановка новой задачи</h1>
      <div class="form-group">
        <label for="exampleFormControlInput1">Заголовок</label>
        <input
          required
          minlength="6"
          v-model="newTask.header"
          type="text"
          class="form-control"
          id="exampleFormControlInput1"
          placeholder="Заголовок новой задачи"
        />
      </div>
      <div class="form-group">
        <label for="exampleFormControlTextarea1">Описание</label>
        <textarea
          class="form-control"
          minlength="15"
          maxlength="2048"
          placeholder="Описание новой задачи..."
          id="exampleFormControlTextarea1"
          v-model="newTask.description"
          rows="3"
        ></textarea>
      </div>
      <div class="countWord align-self-end">осталось {{leftSimbols}} символов</div>
      <label class="mr-sm-2" for="inlineFormCustomSelect">выбрать Тэг задачи</label>
      <div class="d-flex align-content-center flex-wrap">
        <div class="col-2">
          <select v-model="tag" class="custom-select mr-sm-2 mb-5" id="inlineFormCustomSelect">
            <option value="test">Тест</option>
            <option value="mest">Мест</option>
            <option value="rest">Рест</option>
          </select>
        </div>
        <div class="col-2">
          <a @click="addTag()" class="btn btn-outline-dark m-0">{{ tag }}</a>
        </div>
        <div
          class="col-2"
          @dblclick="deleteTag(index)"
          v-for="(item, index) in newTask.taskTags"
          :key="index"
        >
          <div class="btn btn-dark m-0">{{ item.nameTag }}</div>
        </div>
        <div class="col text-danger">{{ error }}</div>
      </div>

      <datepicker class="p-2 col-4"  v-model='newTask.deadLineTask' :bootstrap-styling="true">
        <div slot="beforeCalendarHeader" class="animated-placeholder calender-header">Сроки задачи</div>
      </datepicker>

      <button v-on:click="makeTask()" class="btn btn-primary">Установить задачу</button>
    </div>
  </div>
</template>
<script>
import Datepicker from "vuejs-datepicker";
import auxios from "axios";
export default {
  mounted() {
   
  },
  data() {
    return {
      newTask: {
        description:'',
        taskTags:[
        ]
      },
      tag: "test",
      error: ""
    };
  },
  computed: {
    leftSimbols() {
      return 2048 - this.newTask.description.length;
    }
  },
  methods: {
    makeTask() {
      this.$store.dispatch("newTask", this.newTask);
      let d = new Date(this.newTask.deadLineTask)
       this.newTask.deadLineTask = formatDate(d)
         
      console.log(this.newTask);
      
      //  auxios
      // .post("https://192.168.4.99:32772/api/task",{
      //   body:this.newTask
      // })
      // .then(response => (this.tasks = response.data))
      // .then(response => this.$router.push("/"));
    },
    addTag() {
      console.log(this.newTask.taskTags);
      let isSameTag = this.newTask.taskTags.find(tag => {
        return this.tag == tag.nameTag;
      });
      if (!isSameTag) {
        this.newTask.taskTags.unshift({nameTag:this.tag});
        this.tag = "test";
        this.error = "";
      } else {
        this.error = "Такой Тэг уже существует";
      }
    },
    deleteTag(ind) {
      this.$delete(this.newTask.taskTags, ind);
    }
  },
  components: {
    Datepicker
  }
};
</script>
<style  >
img {
  display: block;
  width: auto;
  height: 20vw;
}
textarea {
  display: block;
}
.btn {
  margin: 2vw 0;
  padding: 1vw 2vw;
  display: block;
}

.calendar {
  position: relative;
  background: black;
}
</style>