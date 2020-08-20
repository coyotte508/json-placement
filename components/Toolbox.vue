<template>
  <v-card dark width="300" :class="['toolbox', vertical, horizontal]">
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
        <v-col><v-switch v-model="horizontal" hide-details false-value="left" true-value="right" label="Right" /></v-col>
        <v-col><v-switch v-model="vertical" hide-details false-value="top" true-value="bottom" label="Bottom" /></v-col>
      </v-row>
    </v-card-text>
    <v-card-actions>
      <v-spacer />
      <v-btn @click="newItem">
        New
      </v-btn>
    </v-card-actions>
    <v-dialog v-model="showDialog" width="500">
      <v-card>
        <v-card-title>New item</v-card-title>
        <v-card-text>
          <v-form ref="form" @submit.prevent="addNew">
            <v-text-field v-model="newId" label="ID" required />
            <v-text-field v-model="newName" label="Name" required />
          </v-form>
        </v-card-text>
        <v-card-actions>
          <v-spacer />
          <v-btn @click="addNew">
            Add
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-card>
</template>

<script lang="ts">
import { Vue, Component, Inject } from 'vue-property-decorator';
import { Grid } from '~/data/grid';

@Component
export default class extends Vue {
  vertical = 'top';
  horizontal = 'left';

  showDialog = false;
  newName = '';
  newId = '';

  newItem () {
    this.newName = '';
    this.newId = '';
    this.showDialog = true;
  }

  addItem () {
    if (this.$refs.form.validate()) {

    }
  }

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
