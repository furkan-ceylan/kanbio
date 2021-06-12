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
          <div class="task-count">3</div>
        </div>
        <div class="card-header-right">
          <button class="material-icons">add</button>
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
          <p>{{ task.text }}</p>
          <div class="task-bottom">
            <div class="task-bottom-left">
              <span class="material-icons task-icons">question_answer</span>
              <h5>12</h5>
              <span class="material-icons task-icons">attach_file</span>
              <h5>5</h5>
            </div>
            <div class="task-bottom-right">
              <button class="btn">Low</button>
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
          <div class="task-count">3</div>
        </div>
        <div class="card-header-right">
          <button class="material-icons">add</button>
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
          <p>{{ task.text }}</p>
          <div class="task-bottom">
            <div class="task-bottom-left">
              <span class="material-icons task-icons">question_answer</span>
              <h5>12</h5>
              <span class="material-icons task-icons">attach_file</span>
              <h5>5</h5>
            </div>
            <div class="task-bottom-right">
              <button class="btn">Low</button>
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
          <div class="task-count">3</div>
        </div>
        <div class="card-header-right">
          <button class="material-icons">add</button>
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
          <p>{{ task.text }}</p>
          <div class="task-bottom">
            <div class="task-bottom-left">
              <span class="material-icons task-icons">question_answer</span>
              <h5>12</h5>
              <span class="material-icons task-icons">attach_file</span>
              <h5>5</h5>
            </div>
            <div class="task-bottom-right">
              <button class="btn">Low</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tasks',
  data: function () {
    return {
      tasks: [
        { id: 0, text: '1', list: 1 },
        { id: 1, text: '2', list: 2 },
        { id: 2, text: '3', list: 2 },
        { id: 3, text: '4', list: 3 },
        { id: 4, text: '5', list: 1 },
        { id: 5, text: '6', list: 3 },
      ],
    }
  },
  methods: {
    getList(list) {
      return this.tasks.filter((task) => task.list == list)
    },

    startDrag(event, task) {
      console.log(task)
      event.dataTransfer.dropEffect = 'move'
      event.dataTransfer.effectAllowed = 'move'
      event.dataTransfer.setData('taskID', task.id)
    },

    onDrop(event, list) {
      const taskID = event.dataTransfer.getData('taskID')
      const task = this.tasks.find((task) => task.id == taskID)
      task.list = list
    },
  },
}
</script>

<style scoped>
.tasks {
  display: flex;
  justify-content: center;
  gap: 13rem;
  margin-bottom: 4rem;
}

.task-card {
  display: flex;
  flex-direction: column;
  background-color: var(--darkest);
  width: 17%;
  min-height: 200px;
  border-radius: 2rem;
  padding-bottom: 1rem;
  box-shadow: rgba(0, 0, 0, 0.56) 0px 22px 70px 4px;
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
  cursor: pointer;
}

.task:hover {
  transition: 0.4s;
  box-shadow: 0px 15px 15px -5px rgba(0, 0, 0, 0.2);
  transform: translate(0, -3px);
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

.btn {
  width: 80px;
  height: 40px;
  border-radius: 2rem;
  background-color: var(--green-btn);
  margin-right: 1rem;
  margin-bottom: 1rem;
  color: var(--white);
  font-weight: bold;
  font-size: 1rem;
  transform: translate(0, 1px);
  transition: 0.2s;
}

.btn:hover {
  transition: 0.2s;
  box-shadow: 0px 15px 15px -5px rgba(0, 0, 0, 0.2);
  transform: translate(0, -1px);
}

.task-icons {
  color: #828390;
}
</style>
