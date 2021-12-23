<script>
export default /*#__PURE__*/ {
  name: "VueMzcCheckbox", // vue component name
  model: {
    prop: "values",
    event: "change",
  },
  props: {
    value: {
      type: [String, Number],
      default: "",
    },
    values: {
      type: [String, Array, Number, Boolean],
      default: "",
    },
  },
  computed: {
    checked() {
      if (this.values instanceof Array) {
        return this.values.includes(this.value);
      }
      return this.values === true;
    },
  },
  methods: {
    change(checked) {
      if (this.values instanceof Array) {
        const changes = [...this.values];

        if (checked) {
          changes.push(this.value);
        } else {
          changes.splice(changes.indexOf(this.value), 1);
        }
        this.$emit("change", changes);
      } else {
        this.$emit("change", checked);
      }
    },
  },
};
</script>

<template>
  <label
    class="vue-mzc-checkbox"
    tabindex="0"
    :class="checked ? 'vue-mzc-checkbox--checked' : ''"
    @keyup.space="() => change(!checked)"
  >
    <input
      class="vue-mzc-checkbox__input"
      type="checkbox"
      tabindex="-1"
      :checked="checked"
      :value="value"
      @change="(e) => change(e.target.checked)"
    />
    <span class="vue-mzc-checkbox__box">
      <i class="vue-mzc-checkbox__icon"></i>
    </span>
    <span v-if="$slots.default" class="vue-mzc-checkbox__title">
      <slot />
    </span>
  </label>
</template>
