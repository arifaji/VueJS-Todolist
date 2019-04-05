<template>
  <div class="about">
    <h1>This is an about page, Dynamicform tryhard</h1>
    <div v-html="formUI()"/>
  </div>
</template>

<script>
export default {
  name: "about",
  components: {},
  data() {
    return {
      data: [],
      model: [
        { key: "name", label: "Name", type: "text" },
        { key: "age", label: "Age", type: "number" },
        { key: "alamat", label: "Alamat", type: "textarea" }
      ]
    };
  },
  methods: {
    formUI() {
      let model = this.model;
      let renderUI = model.map(m => {
        let key = m.key;
        let label = m.label;
        let type = m.type;

        let input = `<input class='form-input' type=${type} key=${key} />`;
        if (type == "textarea") {
          input = `<textarea class='form-control' key=${key}></textarea>`;
        }
        return `<div key=${"g" + key} class="form-group">
            <label class="form-label" key=${"l" + key} htmlFor=${key}>
              ${label}
            </label>
            ${input}
          </div>
        `;
      });

      return renderUI.join("");
    }
  }
};
</script>

<style scoped>
</style>
