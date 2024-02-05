<template>
    <div
      contenteditable
      @input="updateText"
      class="outline-none p-2"
      :contenteditable="isEditable.toString()"
      @dblclick="toggleEditable"
      @keydown.enter.prevent="submitText"
    >
      {{ text }}
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        text: "Editable Text",
        isEditable: false,
      };
    },
    methods: {
      updateText(event) {
        this.text = event.target.innerText;
      },
      toggleEditable() {
        this.isEditable = !this.isEditable;
      },
      submitText() {
        // Handle submitting the text on Enter key if needed
        console.log("Text submitted:", this.text);
        this.isEditable = false
      },
    },
  };
  </script>
  
  <style>
  /* Add your custom styles here if needed */
  </style>
  