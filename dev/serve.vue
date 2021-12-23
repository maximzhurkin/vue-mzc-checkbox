<script>
import Vue from "vue";
import VueMzcCheckbox from "@/vue-mzc-checkbox.vue";
import "../src/vue-mzc-checkbox.css";
import "./serve.css";

export default Vue.extend({
  name: "ServeDev",
  components: {
    VueMzcCheckbox,
  },
  data() {
    return {
      remember: true,
      selected: [
        "Vue.js",
        "JavaScript",
        "CSS",
      ],
    };
  },
});
</script>

<template>
  <div id="app">
    <div class="examples">
      <div class="examples__item">
        <div class="example">
          <div class="example__ui">
            <div class="list">
              <div class="list__item">
                <vue-mzc-checkbox v-model="remember" value="remember">Remember</vue-mzc-checkbox>
              </div>
            </div>
          </div>
          <div class="example__debug">
            <pre>{{ remember }}</pre>
          </div>
        </div>
      </div>
      <div class="examples__item">
        <div class="example">
          <div class="example__ui">
            <div class="list">
              <div class="list__item">
                <vue-mzc-checkbox v-model="selected" value="Vue.js">Vue.js</vue-mzc-checkbox>
              </div>
              <div class="list__item">
                <vue-mzc-checkbox v-model="selected" value="JavaScript">JavaScript</vue-mzc-checkbox>
              </div>
              <div class="list__item">
                <vue-mzc-checkbox v-model="selected" value="HTML">HTML</vue-mzc-checkbox>
              </div>
              <div class="list__item">
                <vue-mzc-checkbox v-model="selected" value="CSS">CSS</vue-mzc-checkbox>
              </div>
            </div>
          </div>
          <div class="example__debug">
            <pre>{{ selected }}</pre>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
