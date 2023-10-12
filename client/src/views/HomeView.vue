<script setup lang="ts">
import { ref } from 'vue';

  const newTask = ref('');
  const tasks = ref([] as {id?:number, text:string, completed:boolean}[]);

  const tabState = ref('current');
  const tabs = ['all', 'current', 'completed'];

  function addTask() {
    tasks.value.push({text:newTask.value, completed:false});
    newTask.value = '';
  };

  function shouldDisplay(task:{id?:number, text:string, completed:boolean}) {
    switch (tabState.value) {
      case 'all':
        return true;
      case 'current':
        return !task.completed;
      case 'completed':
        return task.completed;
    }
  }

</script>

<template>
  <main>
    <h1 class="title" >Home</h1>
    <h2 class="subtitle">
      Welcome to your Vue.js + TypeScript app
    </h2>

    <nav class="panel is-primary">
      <p class="panel-heading">
        To Do
      </p>
      <div class="panel-block">
        <p class="control has-icons-left">
          <input  class="input" type="text" placeholder="What do you want to do"
                  @keypress.enter="addTask" v-model="newTask" >
          <span class="icon is-left">
            <i class="fas fa-plus" aria-hidden="true"></i>
          </span>
        </p>
      </div>
      <p class="panel-tabs">
        <a v-for="tab in tabs" :class="{'is-active':tabState == tab}" @click.prevent="tabState = tab">{{ tab }}</a>
      </p>
      <label class="panel-block" v-for="task in tasks" v-show="shouldDisplay(task)">
        <input type="checkbox" v-model="task.completed">
        {{ task.text}}
      </label>
      <div class="panel-block">
        <button class="button is-link is-outlined is-fullwidth">
          Reset all filters
        </button>
      </div>
    </nav>
  </main>
</template>