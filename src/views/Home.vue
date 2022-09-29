<template>
  <div class="home">
    <div class="container-editor">
      <h1 class="py-4">Code Editor</h1>
      <div class="d-flex container-selected">
        <div>
          <p>Select Languaje</p>
          <select
              v-model="languageId"
              class="form-select"
              style="width: 100%"
              aria-label="Default select example"
              @change="changeLanguage()"
            >
            <option value="70" selected>Python</option>
            <option value="76">C++</option>
            <option value="62">Java</option>
          </select>
        </div>
        <div>
          <p>Select font size</p>
          <select
              v-model="fontId"
              class="form-select"
              style="width: 100%"
              aria-label="Default select example"
              @change="change_font()"
            >
            
            <option v-for="i,index in 40" :value="i" :key="index" selected>{{i}}</option>
          </select>
        </div>
      </div>
      <button class="btn btn-primary mt-3 pt-2" @click="run_program">
        Run Program
      </button>

      <brace
        style="height: 73vh; margin-top: 20px"
        :fontsize="this.current_font + 'px'"
        :theme="'tomorrow'"
        :mode="this.currentLanguage"
        :codefolding="'markbegin'"
        :softwrap="'free'"
        :selectionstyle="'text'"
        :highlightline="true" >
      </brace>
    </div>
  </div>
</template>

<script>
import Brace from "vue-bulma-brace";

export default {
  name: "Home",
  data() {
    return {
      current_font: 12,
      currentLanguage: "python",
      languageId: 70,
      fontId: 12,
      languageMap: {
        70: "python",
        76: "cpp",
        62: "java",
      },
    };
  },
  components: {
    Brace,
  },
  methods: {
    evalue_code() {},
    preprocessing_code() {
      this.line_code = this.code.split("\n");
      console.log(this.line_code);
    },
    change_font() {
      this.current_font = this.fontId;
    },
    changeLanguage() {
      console.log("languageId", this.languageId);
      this.requestBody.language_id = this.languageId.toString();
      this.currentLanguage = this.languageMap[this.languageId];
    },
    // correr el programa
    run_program() {
      
    }
  },
};
</script>
<style lang="scss" scoped>
.container-editor {
  width: 100%;
  height: 100%;
  padding: 0 20px;
}
.container-selected {
  width: 100%;
}

.container-selected div {
  width: 50%;
}

</style>