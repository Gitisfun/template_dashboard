<template>
  <div>
    <label class="dash-text-input-label" :for="name">{{ name }}</label>
    <input class="dash-text-input" placeholder="..." :name="name" :type="type" v-model="innerValue" />
  </div>
</template>

<script>
export default {
  name: "TextInputField",
  props: {
    value: {
      type: String,
      default: "",
    },
    name: {
      type: String,
      default: "",
    },
    type: {
      type: String,
      default: "text",
    },
  },
  data: () => ({
    innerValue: "",
  }),
  watch: {
    // Handles internal model changes.
    innerValue(val) {
      // allows us to use v-model on our input.
      this.$emit("input", val);
    },
    // Handles external model changes.
    value(newVal) {
      this.innerValue = newVal;
    },
  },
  created() {
    if (this.value) {
      this.innerValue = this.value;
    }
  },
};
</script>

<style>
.dash-text-input-label {
  width: 35%;
  color: black;
  font-weight: 500;
  font-size: 18px;
  display: inline-block;
  font-family: "Comic Sans MS", "Comic Sans", cursive;
}
.dash-text-input {
  height: 35px;
  margin-right: 0px;
  margin-left: 0px;
  margin-top: 20px;
  margin-bottom: 0px;
  width: 65%;
  border: none;
  outline: none;
  font-size: 14px;
  background: white;
  border: 1.7px solid grey;
  border-radius: 6px;
  padding: 0 15px;
  resize: none;
}
</style>