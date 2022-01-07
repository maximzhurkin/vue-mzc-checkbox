<script>
export default /*#__PURE__*/ {
  name: "VueMzcCheckbox",
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

<style>
:root {
  --vue-mzc-checkbox-size: 24px;
  --vue-mzc-checkbox-gap: 8px;
  --vue-mzc-checkbox-border-radius: 4px;
  --vue-mzc-checkbox-border-color: #dddddd;
  --vue-mzc-checkbox-border-hover-color: #cccccc;
  --vue-mzc-checkbox-background-color: #ffffff;
  --vue-mzc-checkbox-icon-color: #ffffff;
  --vue-mzc-checkbox-primary-color: #306EC4;
  --vue-mzc-checkbox-primary-hover-color: #3F78C7;
}
.vue-mzc-checkbox {
  cursor: pointer;
  padding-left: 32px;
  padding-left: calc(var(--vue-mzc-checkbox-size) + var(--vue-mzc-checkbox-gap));
  display: inline-block;
  position: relative;
  min-height: 24px;
  min-height: var(--vue-mzc-checkbox-size);
}
.vue-mzc-checkbox__input {
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0 0 0 0);
  position: absolute;
  width: 1px;
  height: 1px;
  border: 0;
  z-index: -1000;
}
.vue-mzc-checkbox__box {
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 24px;
  height: 24px;
  width: var(--vue-mzc-checkbox-size);
  height: var(--vue-mzc-checkbox-size);
  position: absolute;
  top: 0;
  left: 0;
  border: 1px solid #dddddd;
  border-color: var(--vue-mzc-checkbox-border-color);
  background-color: #ffffff;
  background-color: var(--vue-mzc-checkbox-background-color);
  border-radius: 4px;
  border-radius: var(--vue-mzc-checkbox-border-radius);
  transition: border-color 0.25s ease-in-out, background-color 0.25s ease-in-out;
}
.vue-mzc-checkbox__icon {
  display: block;
  width: 12px;
  height: 10px;
  fill: #ffffff;
  fill: var(--vue-mzc-checkbox-icon-color);
  opacity: 0;
  background-image: url("data:image/svg+xml,%3Csvg class='vue-mzc-checkbox__icon' width='12' height='10' xmlns='http://www.w3.org/2000/svg' %3E%3Cpath fill-rule='evenodd' clip-rule='evenodd'%0Afill='%23ffffff' d='M4 10 0 5.954l1.886-1.908L4 6.186 10.114 0 12 1.907 4 10Z' /%3E%3C/svg%3E");
}
.vue-mzc-checkbox__title {
  display: inline-block;
  user-select: none;
  font-size: 16px;
  line-height: 24px;
}
.vue-mzc-checkbox__input:checked + .vue-mzc-checkbox__box {
  background-color: #306EC4;
  background-color: var(--vue-mzc-checkbox-primary-color);
  border-color: #306EC4;
  border-color: var(--vue-mzc-checkbox-primary-color);
}
.vue-mzc-checkbox__input:checked + .vue-mzc-checkbox__box > .vue-mzc-checkbox__icon {
  opacity: 1;
}
@media (hover: hover) {
  .vue-mzc-checkbox:hover .vue-mzc-checkbox__box {
    border-color: #cccccc;
    border-color: var(--vue-mzc-checkbox-border-hover-color);
  }
  .vue-mzc-checkbox--checked:hover .vue-mzc-checkbox__box {
    background-color: #3F78C7;
    background-color: var(--vue-mzc-checkbox-primary-hover-color);
    border-color: #306EC4;
    border-color: var(--vue-mzc-checkbox-primary-color);
  }
}
</style>