<template>
  <q-page class="bg-grey-3 column">

    <q-list 
      class="bg-white"
      separator
      bordered>
      <q-item
        v-for="task in tasks"
        :key="task.title"
        @click="task.done = !task.done"
        :class="{ 'done bg-green-1': task.done }"
        clickable
        v-ripple>
        <q-item-section avatar>
          <q-checkbox 
            v-model="task.done" 
            class="no-pointer-events"
            color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section
          v-if="task.done"
          side>
          x
        </q-item-section>
      </q-item>

    </q-list>

  </q-page>
</template>

<script lang="ts">
import ExampleComponent from '../components/ClassComponent.vue'
import { Vue, Component } from 'vue-property-decorator'

@Component({
  components: { ExampleComponent }
})
export default class PageIndex extends Vue {
  data() {
    return {
      tasks: [
      {
        title: 'Get bananas',
        done: false
      },
      {
        title: 'Eat bananas',
        done: false
      },
      {
        title: 'Poo bananas',
        done: false
      }
    ]
    }
  }
}
</script>

<style lang="scss">
  .done {
    .q-item__label {
      text-decoration: line-through;
      color: #bbb;
    }
  }
</style>
