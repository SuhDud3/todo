<template>
  <div class="search">
    <input
    type="text"
    v-model="search"
    placeholder="New task..."
    />
  </div>
  <div class="add">
    <button @click="addItem">Add Task</button>
  </div>
  <li v-for="item in itemList" :key="item.id">
    <input type="checkbox" :id="item.id" :checked="item.done" @change="toggleItem(item.id)">
    <label :for="item.id">{{ item.text }}</label>
    <button @click="deleteItem(item.id)">Delete</button>
  </li>
</template>
<script>
export default {
  data() {
    return {
      search: "",
      itemList : [],
    };
  },
  methods: {
    addItem() {
      this.itemList.push({
        id: Date.now(),
        text: this.search,
        done: false,
      });
    },
    deleteItem(id) {
      this.itemList = this.itemList.filter((item) => item.id !== id);
    },
    toggleItem(id) {
      this.itemList = this.itemList.map((item) => {
        if (item.id === id) {
          item.done = !item.done;
        }
        return item;
      });
    },
  },
}
</script>
<style scoped>
li {
  list-style: none;
  margin: 0.5rem 0;
}

button {
  background-image: linear-gradient(#f7f8fa ,#e7e9ec);
  border-color: #adb1b8 #a2a6ac #8d9096;
  border-style: solid;
  border-width: 1px;
  border-radius: 3px;
  box-shadow: rgba(255,255,255,.6) 0 1px 0 inset;
  box-sizing: border-box;
  color: #0f1111;
  cursor: pointer;
  display: inline-block;
  font-family: "Amazon Ember",Arial,sans-serif;
  font-size: 14px;
  height: 29px;
  font-size: 13px;
  outline: 0;
  overflow: hidden;
  padding: 0 11px;
  text-align: center;
  text-decoration: none;
  text-overflow: ellipsis;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  white-space: nowrap;
}

button:active {
  border-bottom-color: #a2a6ac;
}

button:active:hover {
  border-bottom-color: #a2a6ac;
}

button:hover {
  border-color: #a2a6ac #979aa1 #82858a;
}

button:focus {
  border-color: #e77600;
  box-shadow: rgba(228, 121, 17, .5) 0 0 3px 2px;
  outline: 0;
}


</style>