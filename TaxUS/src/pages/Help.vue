<template>
  <q-page class="q-pa-lg">
    <h5 class="q-mt-none">Help</h5>
    <p>This application help to your taxes accounting.</p>
  </q-page>
</template>

<script lang="ts">
import ExampleComponent from '../components/ClassComponent.vue'
import { Vue, Component } from 'vue-property-decorator'

@Component({
  components: { ExampleComponent }
})
export default class PageIndex extends Vue {

}
</script>
