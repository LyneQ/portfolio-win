<script lang="ts">
import {defineComponent} from 'vue'

export default defineComponent({
  name: "default",
  methods: {
    getDate: () => getDate(),
    getTime: () => getTime(),
    changeTheme: () => changeTheme()
  }
})

const getDate = () => {
  const date = new Date();
  return `${date.getDate()}-${date.getMonth() + 1}-${date.getFullYear().toString().slice(2)}`
};

const getTime = () => {
  const date = new Date();
  const hours = date.getHours();
  const minutes = date.getMinutes();
  return `${hours}:${minutes}`
};

const changeTheme = () => {
  const body = document.querySelector('body');

  if (!body) throw new Error('Body not found');

  body.classList.contains('light-theme')
      ? body.classList.replace('light-theme', 'dark-theme')
      : body.classList.replace('dark-theme', 'light-theme');
}
</script>

<template>
    <nav class="taskbar">
      <ul class="taskbar_icons">
        <li class="taskbar_icons_item active">
          <i class="fas fa-home"></i>
        </li>
        <li class="taskbar_icons_item">
          <i class="fas fa-cloud"></i>
        </li>
      </ul>

      <ul class="taskbar_tools">
        <li class="taskbar_tools_item"  @click="changeTheme">
          <i class="fas fa-moon"></i>
        </li>
        <li class="taskbar_tools_item">
          <i class="fas fa-battery-full"></i>
        </li>
        <li class="taskbar_tools_item">
          <i class="fas fa-volume-up"></i>
        </li>
        <li class="taskbar_tools_item">
          <i class="fas fa-wifi"></i>
        </li>
        <li class="taskbar_tools_item">
          <i class="fas fa-language"></i>
        </li>
        <li class="taskbar_tools_item date-time">
          {{ getTime() }}
          <br/>
          {{ getDate() }}
        </li>
      </ul>
    </nav>
    <NuxtPage/>
</template>

<style scoped lang="scss">
@use "~/assets/scss/variables.scss" as *;

.taskbar {
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 50px;
  background-color: var(--taskbar);
  display: flex;
  justify-content: center;
  align-items: center;

  li {
    list-style: none;
    min-width: 40px;
    height: 40px;
      i {
        color: var(--text) !important;
      }

    &.date-time {
      text-align: right;
      color: var(--text);
    }
  }

  & .taskbar_icons {
    padding: 1rem;
    display: flex;
    gap: 10px;

    & .taskbar_icons_item {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 40px;
      height: 40px;

      border-radius: 5px;
      transition: background-color 0.3s;
      cursor: pointer;
      &.active {
        background-color: var(--border);
      }

      &:hover {
        background-color: #555;
      }

      & i {
        color: #fff;
        font-size: 20px;
      }
    }
  }

  & .taskbar_tools {
    padding: 1rem;
    display: flex;
    gap: 10px;
    position: absolute;
    right: 0;

    & .taskbar_tools_item {
      display: flex;
      justify-content: center;
      align-items: center;
      color:var(--text);
      font-size: 12px;
      padding: 4px;

      min-width: auto;
      height: auto;

      border-radius: 5px;
      transition: background-color 0.3s;
      cursor: pointer;

      &:hover {
        background-color: #555;
      }

      & i {
        color: #fff;
        font-size: 12px;
      }
    }
  }
}
</style>