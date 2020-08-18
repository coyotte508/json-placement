<template>
  <v-card dark width="300" :class="['toolbox', vertical, horizontal]">
    <v-card-title>Settings</v-card-title>
    <v-card-text>
      <v-row>
        <v-col>
          <v-text-field v-model="grid.width" hide-details label="Width" type="number" />
        </v-col>
        <v-col>
          <v-text-field v-model="grid.height" hide-details label="Height" type="number" />
        </v-col>
      </v-row>
      <v-row>
        <v-col><v-switch v-model="horizontal" false-value="left" true-value="right" label="Right" /></v-col>
        <v-col><v-switch v-model="vertical" false-value="top" true-value="bottom" label="Bottom" /></v-col>
      </v-row>
    </v-card-text>
  </v-card>
</template>

<script lang="ts">
import { Vue, Component, Inject } from 'vue-property-decorator';
import { Grid } from '~/data/grid';

@Component
export default class extends Vue {
  vertical = 'top';
  horizontal = 'left';

  @Inject()
  grid!: Grid;
}
</script>

<style lang="scss">
.toolbox {
  position: absolute;
  transition: 400ms ease-in-out;

  &.top {
    top: 10px;
  }

  &.bottom {
    bottom: 10px;
  }

  &.left {
    left: 10px;
  }

  &.right {
    right: 10px;
  }
}
</style>
