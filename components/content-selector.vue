<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "content-selector",
  props: {
    name: {
      type: String,
      required: true
    }
  },
  setup(props) {
    const availablePage = ['index', 'about', 'contact', 'projects'];

    if (!availablePage.includes(props.name)) {
      throw new Error(`Page ${props.name} do not exist`)
    }
    return {
      name: props.name
    }
  },

  methods: {
    minimizeWindow() {
      console.log('minimize')
    },
    maximizeWindow() {
      console.log('maximize')
    },
    closeWindow() {
      console.log('close')
    }
  }
})
</script>

<template>
  <div class="container">
    <section id="window">
      <div id="window-header">
        <h6 id="window-title"> <i class="fas fa-home"></i> {{ name }}</h6>
        <div id="window-header-buttons">
          <div class="window-header-button" @click="minimizeWindow"><i class="fa-solid fa-minus"></i></div>
          <div class="window-header-button" @click="maximizeWindow"><i class="fa-regular fa-square"></i></div>
          <div class="window-header-button" @click="closeWindow"><i class="fa-solid fa-xmark"></i></div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped lang="scss">

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#window {
  width: 85vw;
  height: 85vh;
  background-color: var(--border);
  border: 2px solid var(--primary);
  border-radius: $border-radius;

  #window-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem;
    background-color: var(--background);
    border-top-left-radius: $border-radius;
    border-top-right-radius: $border-radius;

    #window-title {
      color: var(--text);
      display: flex;
      align-items: center;
      gap: 0.5rem;
      margin: 5px 10px;
    }

    #window-header-buttons {
      display: flex;
      gap: 0.5rem;
    }
  }
}

</style>