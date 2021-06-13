<template>
  <div id="openModal" class="modalDialog">
    <div>
      <a href="#close" title="Close" class="close">
        <span class="material-icons">close</span></a
      >
      <div class="add-task">
        <div class="add-task-title">
          <h2>Add a new task</h2>
        </div>
        <div class="add-task-content">
          <textarea
            type="text"
            placeholder="Task description"
            v-model="text"
            required
          />
          <select name="Priority" id="Priority" v-model="priority" required>
            <option value="" disabled selected>Priority</option>
            <option value="Low">Low</option>
            <option value="Medium">Medium</option>
            <option value="High">High</option>
          </select>
          <select
            name="list"
            id="list"
            v-model="list"
            required
            @change="switchView($event, $event.target.selectedIndex)"
          >
            <option value="" disabled selected>List</option>
            <option value="To Do">To Do</option>
            <option value="Doing">Doing</option>
            <option value="Done">Done</option>
          </select>
          <button class="btn btnBlue" @click.prevent="addTask()" href="#close">
            Add
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddTask',
  data: function () {
    return {
      id: '1',
      text: '',
      list: '',
      priority: '',
      comments: 0,
      selectedIndex: '',
    }
  },
  methods: {
    switchView: function (event, selectedIndex) {
      console.log(event, selectedIndex)
      this.selectedIndex = selectedIndex
    },
    addTask() {
      const id = Math.floor(Math.random() * 100000)
      const text = this.text
      const list = this.selectedIndex
      const priority = this.priority
      const comments = this.comments
      if (!text || !list || !priority) {
        alert('Please fill all the fields')
        return
      }
      this.$emit('create-task', {
        id,
        text,
        list,
        priority,
        comments,
      })

      this.text = ''
      this.list = ''
      this.priority = ''
    },
  },
}
</script>

<style scoped>
.modalDialog {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 99999;
  opacity: 0;
  -webkit-transition: opacity 0.3s ease;
  -moz-transition: opacity 0.3s ease;
  transition: opacity 0.3s ease;
  pointer-events: none;
  display: flex;
  flex-direction: column;
  min-height: 200px;
  border-radius: 2rem;
  padding-bottom: 2rem;
  box-shadow: rgba(0, 0, 0, 0.56) 0px 22px 70px 4px;
}

.modalDialog:target {
  opacity: 1;
  pointer-events: auto;
}

.modalDialog > div {
  width: 400px;
  height: 400px;
  position: relative;
  margin: 6% auto;
  padding: 5px 20px 13px 20px;
  border-radius: 10px;
  background-color: var(--darkest);
}

.close {
  color: #ffffff;
  line-height: 25px;
  position: absolute;
  right: 15px;
  text-align: center;
  top: 15px;
  width: 24px;
  text-decoration: none;
  font-weight: bold;
  -webkit-border-radius: 12px;
  -moz-border-radius: 12px;
  border-radius: 12px;
  -moz-box-shadow: 1px 1px 3px #000;
  -webkit-box-shadow: 1px 1px 3px #000;
  box-shadow: 1px 1px 3px #000;
  transition: all 0.3s ease;
}

.add-task {
  padding: 1rem;
  color: white;
  overflow: hidden;
}

.add-task-title {
  margin-bottom: 2rem;
}

.add-task-content {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.add-task-content textarea {
  background-color: var(--dark);
  width: 100%;
  height: 80px;
  color: white;
  font-size: 1.3rem;
}

.add-task-content select {
  background-color: var(--dark);
  width: 100%;
  height: 40px;
  color: white;
  font-size: 1rem;
}

.add-task-content button {
  right: 0;
  margin-left: auto;
  margin-top: 1rem;
}
</style>
