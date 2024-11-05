<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <TestApp msg="Test app"/>
    <div>
      <input
          type="text"
          v-model="inputText"
          @input="filterSuggestions"
          placeholder="Type something..."
      />
      <ul v-if="filteredSuggestions.length > 0">
        <li v-for="(suggestion, index) in filteredSuggestions" :key="index" @click="selectSuggestion(suggestion)">
          {{ suggestion.name }}
        </li>
      </ul>
      <p>You typed: {{ inputText }}</p>
    </div>
  </div>
</template>
<script>
import TestApp from './components/TestApp.vue'

export default {
  name: 'App',
  components: {
    TestApp
  },
  data() {
    return {
      inputText: "",
      items: [
        {
          id: 1,
          name: 'Book'
        },
        {
          id: 2,
          name: 'Pencil'
        },
        {
          id: 3,
          name: 'Apple'
        },
        {
          id: 4,
          name: 'Notebook'
        },
        {
          id: 5,
          name: 'Pen'
        },
        {
          id: 6,
          name: 'Banana'
        },
        {
          id: 7,
          name: 'Eraser'
        },
        {
          id: 8,
          name: 'Orange'
        },
        {
          id: 9,
          name: 'Marker'
        },
        {
          id: 10,
          name: 'Laptop'
        },
        {
          id: 1001,
          name: 'Backpack'
        },
        {
          id: 1002,
          name: 'Avocado'
        }
      ],
      filteredSuggestions: []
    };
  },
  methods: {
    filterSuggestions() {
      this.filteredSuggestions = this.items.filter(item => {
        return item.name.toLowerCase().includes(this.inputText.toLowerCase());
      });
    },

    selectSuggestion(suggestion) {
      this.inputText = suggestion.name;
      this.filteredSuggestions = [];
    }
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  cursor: pointer;
  padding: 5px;
  background-color: #f0f0f0;
  border: 1px solid #ccc;
}

li:hover {
  background-color: #e0e0e0;
}
</style>
