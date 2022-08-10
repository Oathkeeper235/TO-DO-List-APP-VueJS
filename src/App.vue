<template>
  <div class="container">
    <AppHeader :disable="disable" @toggle-add-list="toggleAddList" title="TO DO LIST" />
    <div v-show="showAddList">
      <AddList @add-list="addList" />
    </div>
    <AppLists @toggle-reminder="toggleReminder" @delete-list="deleteList" :lists="lists" />
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppLists from './components/AppLists.vue'
import AddList from './components/AddList.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppLists,
    AddList
  },

  data() {
    return {
      lists: [],
      showAddList: false,
      disable: true
    }
  },

  methods: {
    toggleAddList() {
      this.showAddList = !this.showAddList
    },

    addList(list) {
      this.lists = [...this.lists, list]

      if(this.lists.length > 5) {
        this.toggleAddList()
        this.disable = false
      }
    },

    deleteList(id) {
      if (confirm('Are you sure?')) {
        this.lists = this.lists.filter((list) => list.id !== id)
        this.disable = true
      }
    },

    toggleReminder(id) {
      this.lists = this.lists.map((list) => list.id === id ? { ...list, reminder: !list.reminder } : list)
    }
  },

  created() {
    this.lists = [
      {
        id: 1,
        text: 'List 1',
        color: 'red',
        reminder: true,
      },
      {
        id: 2,
        text: 'List 2',
        color: 'green',
        reminder: true,
      },
      {
        id: 3,
        text: 'List 3',
        color: 'blue',
        reminder: false,
      },
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 25px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
