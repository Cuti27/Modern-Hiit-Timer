<template>
  <div
    :class="{
      NumberLabel: true,
      'font-size-s': checkSizeS,
      'font-size-m': checkSizeM,
      'font-size-l': checkSizeL,
    }"
  >
    <div class="number">
      {{ value }}
    </div>
    <span class="label" v-if="label">{{ computedLabel }}</span>
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    upper: Boolean,
    value: {
      type: Number,
      required: true,
    },
    size: {
      type: String,
      default: "S",
      validator: function (value) {
        // The value must match one of these strings
        console.log("[DEBUG]", value);
        return ["S", "M", "L"].includes(value.toUpperCase());
      },
    },
  },
  computed: {
    computedLabel() {
      return this.upper ? this.label.toUpperCase() : this.label;
    },
    checkSizeS() {
      return this.size && this.size.toUpperCase() === "S";
    },
    checkSizeM() {
      return this.size && this.size.toUpperCase() === "M";
    },
    checkSizeL() {
      return this.size && this.size.toUpperCase() === "L";
    },
  },
};
</script>

<style lang="scss" scoped>
.NumberLabel {
  .number {
    margin-bottom: 5px;
  }

  .label {
    padding-top: 15px;
  }
}

.font-size-s {
  .number {
    font-size: 25px;
  }
  margin-left: 5px;
  margin-right: 5px;
  font-size: 15px;
}
.font-size-m {
  .number {
    font-size: 35px;
  }
  margin-left: 10px;
  margin-right: 10px;
  font-size: 25px;
}
.font-size-l {
  .number {
    font-size: 45px;
  }
  margin-left: 15px;
  margin-right: 15px;
  font-size: 35px;
}
</style>