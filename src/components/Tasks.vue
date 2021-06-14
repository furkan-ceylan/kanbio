.<template>
  <div class="tasks">
    <div
      class="task-card"
      @drop="onDrop($event, 1)"
      @dragenter.prevent
      @dragover.prevent
    >
      <div class="card-header">
        <div class="card-header-left">
          <h2>To Do</h2>
          <div class="task-count">2</div>
        </div>
        <div class="card-header-right">
          <a href="#openModal" class="material-icons">add</a>
        </div>
      </div>
      <div class="card-content">
        <div
          class="task"
          v-for="task in getList(1)"
          :key="task.id"
          draggable="true"
          @dragstart="startDrag($event, task)"
        >
          <div class="card-content-top">
            <div class="card-content-text">
              <p>{{ task.text }}</p>
            </div>
            <div class="card-content-edit">
              <!-- <a href="#openModal2" class="material-icons">edit</a> -->
            </div>
          </div>
          <div class="task-bottom">
            <div class="task-bottom-left">
              <span class="material-icons task-icons">question_answer</span>
              <h5>{{ task.comments }}</h5>
            </div>
            <div class="task-bottom-right">
              <button
                class="btn"
                :class="{
                  btnLow: task.priority === 'Low',
                  btnMedium: task.priority === 'Medium',
                  btnHigh: task.priority === 'High',
                }"
              >
                {{ task.priority }}
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div
      class="task-card"
      @drop="onDrop($event, 2)"
      @dragenter.prevent
      @dragover.prevent
    >
      <div class="card-header">
        <div class="card-header-left">
          <h2>Doing</h2>
          <div class="task-count">2</div>
        </div>
        <div class="card-header-right">
          <a href="#openModal" class="material-icons">add</a>
        </div>
      </div>
      <div class="card-content">
        <div
          class="task"
          v-for="task in getList(2)"
          :key="task.id"
          draggable="true"
          @dragstart="startDrag($event, task)"
        >
          <div class="card-content-top">
            <div class="card-content-text">
              <p>{{ task.text }}</p>
            </div>
            <div class="card-content-edit">
              <!-- <a href="#openModal2" class="material-icons">edit</a> -->
            </div>
          </div>
          <div class="task-bottom">
            <div class="task-bottom-left">
              <span class="material-icons task-icons">question_answer</span>
              <h5>{{ task.comments }}</h5>
            </div>
            <div class="task-bottom-right">
              <button
                class="btn"
                :class="{
                  btnLow: task.priority === 'Low',
                  btnMedium: task.priority === 'Medium',
                  btnHigh: task.priority === 'High',
                }"
              >
                {{ task.priority }}
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div
      class="task-card"
      @drop="onDrop($event, 3)"
      @dragenter.prevent
      @dragover.prevent
    >
      <div class="card-header">
        <div class="card-header-left">
          <h2>Done</h2>
          <div class="task-count">2</div>
        </div>
        <div class="card-header-right">
          <a href="#openModal" class="material-icons">add</a>
        </div>
      </div>
      <div class="card-content">
        <div
          class="task"
          v-for="task in getList(3)"
          :key="task.id"
          draggable="true"
          @dragstart="startDrag($event, task)"
        >
          <div class="card-content-top">
            <div class="card-content-text">
              <p>{{ task.text }}</p>
            </div>
            <div class="card-content-edit">
              <!-- <a href="#openModal2" class="material-icons">edit</a> -->
            </div>
          </div>
          <div class="task-bottom">
            <div class="task-bottom-left">
              <span class="material-icons task-icons">question_answer</span>
              <h5>{{ task.comments }}</h5>
            </div>
            <div class="task-bottom-right">
              <button
                class="btn"
                :class="{
                  btnLow: task.priority === 'Low',
                  btnMedium: task.priority === 'Medium',
                  btnHigh: task.priority === 'High',
                }"
              >
                {{ task.priority }}
              </button>
            </div>
          </div>
        </div>
      </div>
      <AddTask @create-task="addTask" />
    </div>
  </div>
</template>

<script>
import AddTask from '../components/AddTask.vue'

export default {
  name: 'Tasks',
  components: { AddTask },
  data: function () {
    return {
      tasks: [
        {
          id: 0,
          text: 'task count düzenle',
          list: 1,
          priority: 'High',
          comments: 5,
        },
        {
          id: 1,
          text: 'task ekleme',
          list: 2,
          priority: 'Low',
          comments: 3,
        },
        {
          id: 2,
          text: 'task card ekleme',
          list: 2,
          priority: 'Medium',
          comments: 15,
        },
        {
          id: 3,
          text: 'task board ekleme',
          list: 3,
          priority: 'Medium',
          comments: 2,
        },
        {
          id: 4,
          text: 'header fonksiyon butonlarını düzenle',
          list: 1,
          priority: 'Medium',
          comments: 4,
        },
        {
          id: 5,
          text: 'task detayına gitme',
          list: 3,
          priority: 'Low',
          comments: 7,
        },
      ],
      openModal: false,
    }
  },
  methods: {
    getList(list) {
      return this.tasks.filter((task) => task.list == list)
    },

    getListCount(list) {
      return this.tasks.filter((task) => task.list == list.lenght)
    },

    startDrag(event, task) {
      event.dataTransfer.dropEffect = 'move'
      event.dataTransfer.effectAllowed = 'move'
      event.dataTransfer.setData('taskID', task.id)
    },

    onDrop(event, list) {
      const taskID = event.dataTransfer.getData('taskID')
      const task = this.tasks.find((task) => task.id == taskID)
      task.list = list
    },
    addTask(addTask) {
      this.tasks.push(addTask)
    },
  },
}
</script>

<style scoped>
.tasks {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: 13rem;
}

.task-card {
  display: flex;
  flex-direction: column;
  background-color: var(--darkest);
  width: 18%;
  min-height: 200px;
  border-radius: 2rem;
  padding-bottom: 2rem;
  box-shadow: rgba(0, 0, 0, 0.6) 0px 22px 70px 4px;
}

.card-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.5rem;
}

.card-header-left {
  display: flex;
  align-items: center;
  justify-content: center;
}

.task-count {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--light);
  border-radius: 40%;
  color: var(--white);
  width: 40px;
  height: 30px;
  margin-left: 1.5rem;
}

.card-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 1rem;
}

.card-content-top {
  display: flex;
  flex-direction: row;
}

.card-content-edit {
  right: 0;
  margin-left: auto;
  align-items: center;
  padding-right: 1rem;
  padding-top: 1rem;
  opacity: 0;
  transition: 0.4s;
}

.task {
  display: flex;
  flex-direction: column;
  background-color: var(--light);
  width: 90%;
  min-height: 100px;
  border-radius: 1.5rem;
  margin-top: 1rem;
  transform: translate(0, 3px);
  transition: 0.4s;
  cursor: move;
}

.task:hover {
  transition: 0.4s;
  box-shadow: 0px 15px 15px -5px rgba(0, 0, 0, 0.6);
  transform: translate(0, -3px);
}

.task:hover .card-content-edit {
  opacity: 1;
  transition: 0.4s;
}

.task p {
  color: var(--white);
  font-size: 1.3rem;
  padding: 1em;
}

.task-bottom {
  display: flex;
  justify-content: space-between;
}

.task-bottom-left {
  display: flex;
  justify-content: center;
  align-items: center;
}

.task-bottom-left h5 {
  margin-left: 0.25rem;
}

.task-icons {
  margin-left: 1rem;
}

.task-icons {
  color: #828390;
}

@media only screen and (max-width: 1500px) {
  .btn {
    width: 60px;
    height: 30px;
    font-size: 0.85rem;
  }
}

@media only screen and (max-width: 1250px) {
  .tasks {
    flex-direction: column;
    align-items: center;
    gap: 5rem;
  }

  .task-card {
    width: 80%;
  }
}
</style>
