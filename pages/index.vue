<template>
  <div>
    <div class="text-center">
      <svg style="background-color: white; height: calc(100vh - 72px)" :viewBox="`${-grid.width/2} ${-grid.height/2} ${grid.width} ${grid.height}`" />
    </div>
    <Toolbox />
  </div>
</template>

<script lang="ts">
import { Vue, Component, Provide } from 'vue-property-decorator';
import Toolbox from '../components/Toolbox.vue';
import { Grid } from '../data/grid';

@Component({
  components: {
    Toolbox
  }
})
export default class extends Vue {
  @Provide()
  grid: Grid = {
    width: 400,
    height: 600
  }
}
</script>
