<template>
  <div id="app">
    <h1>Vue 3 Conditional Rendering and Form Input Handling</h1>

    <!-- v-if and v-else are used for conditional rendering -->
    <!-- When the button is clicked, the 'toggleMessage' method is triggered -->
    <button @click="toggleMessage">Toggle Message</button>

    <!-- This paragraph will only show when 'showMessage' is true -->
    <p v-if="showMessage">Hello, SIT120!</p>
    <!-- This paragraph will only show when 'showMessage' is false -->
    <p v-else>No message to show, using v-else</p>

    <!-- v-show is similar to v-if but always renders the element in the DOM (with a display CSS property) -->
    <p v-show="showMessage">This is a message that is controlled by v-show</p>

    <!-- v-for is used for rendering a list of items -->
    <!-- v-if within v-for is used to conditionally render items in the list -->
    <ul>
      <li v-for="(item, index) in list" :key="index">
        <span v-if="item.show">{{ item.message }}</span>
      </li>
    </ul>

    <!-- v-model is used for two-way data binding -->
    <!-- The form triggers the 'submitForm' method when submitted -->
    <form @submit.prevent="submitForm">
      <label for="input">Type your name:</label>
      <input type="text" id="input" v-model="inputValue" />
      <button type="submit">Submit</button>
    </form>
    <!-- The value of 'inputValue' is rendered here -->
    <p>Your input: {{ inputValue }}</p>
  </div>
</template>

<script>
export default {
  name: 'WebPage',
  data() {
    return {
      showMessage: true, // this property will control whether to show the message or not
      // this list of items will be used with v-for for list rendering
      list: [
        { message: 'Item 1', show: true },
        { message: 'Item 2', show: false },
        { message: 'Item 3', show: true },
      ],
      inputValue: '', // this will store the value of the input field
    };
  },
  methods: {
    // this method toggles the value of 'showMessage'
    toggleMessage() {
      this.showMessage = !this.showMessage;
    },
    // this method is triggered when the form is submitted
    submitForm() {
      alert('Form submitted with value: ' + this.inputValue);
    },
  },
};
</script>

<!-- CSS styling for the webpage -->
<style scoped>

#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  font-family: Arial, sans-serif;
  background-color: #f8f8f8;
  color: #333;
  text-align: center;
  padding: 2rem;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 2rem;
}

button {
  padding: 0.5rem 1rem;
  margin-top: 1rem;
  border: none;
  border-radius: 4px;
  background-color: #333;
  color: #fff;
  cursor: pointer;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #666;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  margin: 2rem 0;
}

input[type="text"] {
  padding: 0.5rem;
  border-radius: 4px;
  border: 1px solid #ccc;
  width: 100%;
  max-width: 300px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  background-color: #fff;
  border-radius: 4px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
  padding: 1rem;
  margin-bottom: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

@media (min-width: 600px) {
  #app {
    padding: 2rem 4rem;
  }
}
</style>
