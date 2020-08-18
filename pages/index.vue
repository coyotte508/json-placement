<template>
  <div>
    <div class="text-center">
      <svg style="background-color: white; height: calc(100vh - 72px)" :viewBox="`${-grid.width/2} ${-grid.height/2} ${grid.width} ${grid.height}`">
        <line
          :x1="-grid.width/2"
          :x2="grid.width/2"
          y1="0"
          y2="0"
          class="axis"
          :stroke-width="grid.width/700"
        />
        <line
          x1="0"
          x2="0"
          :y1="-grid.height/2"
          :y2="grid.height/2"
          class="axis"
          :stroke-width="grid.width/700"
        />
        <line
          v-for="x in xTicks"
          :key="'vertical-' + x"
          stroke="black"
          :stroke-width="grid.width/2000"
          :x1="x"
          :x2="x"
          :y1="-grid.height/2"
          :y2="grid.height/2"
        />
        <line
          v-for="y in yTicks"
          :key="'hozirontal-' + y"
          stroke="black"
          :stroke-width="grid.width/2000"
          :y1="y"
          :y2="y"
          :x1="-grid.width/2"
          :x2="grid.width/2"
        />
      </svg>
    </div>
    <Toolbox />
  </div>
</template>

<script lang="ts">
import { Vue, Component, Provide } from 'vue-property-decorator';
import { range } from 'lodash';
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
    height: 600,
    ticks: {
      spacing: 10
    }
  }

  get xTicks () {
    return [
      ...range(Math.floor(this.grid.width / this.grid.ticks.spacing)).map(x => -(x + 1) * this.grid.ticks.spacing),
      ...range(Math.floor(this.grid.width / this.grid.ticks.spacing)).map(x => (x + 1) * this.grid.ticks.spacing)
    ];
  }

  get yTicks () {
    return [
      ...range(Math.floor(this.grid.height / this.grid.ticks.spacing)).map(y => -(y + 1) * this.grid.ticks.spacing),
      ...range(Math.floor(this.grid.height / this.grid.ticks.spacing)).map(y => (y + 1) * this.grid.ticks.spacing)
    ];
  }
}
</script>
<style lang="scss">
svg {
  line.axis {
    stroke: black;
  }
}
</style>
