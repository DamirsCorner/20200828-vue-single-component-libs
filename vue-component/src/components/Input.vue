<template>
  <div>
    <label :for="id">{{ label }}</label>
    <input
      class="input"
      :id="id"
      type="text"
      name="id"
      v-model="value"
      @input="change"
    />
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({
  model: {
    prop: "value",
    event: "change",
  },
})
export default class Button extends Vue {
  @Prop({ type: String, required: true }) readonly label!: string;
  @Prop({ type: String, required: true }) readonly id!: string;
  @Prop({ type: String, required: true }) readonly value!: string;

  change() {
    this.$emit("change", this.value);
  }
}
</script>

<style scoped>
.input {
  border-color: black;
  border-width: 1px;
  margin-left: 5px;
}
</style>
