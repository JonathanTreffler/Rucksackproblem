<template>
    <md-app md-waterfall md-mode="flexible">
      <md-app-toolbar class="md-large md-primary">
        <div class="md-toolbar-row">
          <div class="md-toolbar-section-start">
          </div>
        </div>

        <div class="md-toolbar-row md-toolbar-offset">
          <span class="md-display-1">Rucksackproblem</span>
        </div>
      </md-app-toolbar>

      <md-app-content>
        <md-field>
          <label>Single</label>
          <md-file @md-change="fileSelected" />
        </md-field>
      </md-app-content>
    </md-app>
</template>

<style>
  html, body, #__nuxt, #__layout, #__layout > div, .md-app-container {
    min-height: 100vh;
    max-width: 100vw;
  }
  .md-app {
    border: 1px solid rgba(#000, .12);
  }
  .md-app-toolbar {
    height: 196px;
  }
  .md-drawer {
    width: 230px;
    max-width: calc(100vw - 125px);
  }
</style>

<script>
export default {
  data: () => ({
    inputFile: "",
    n: false,
    capacity: false,
  }),
  methods: {
    fileSelected(event) {
      console.log("test");
      console.log(event);
      let file = event[0];

      let reader = new FileReader();

      reader.readAsText(file);

      reader.onload = function() {
        console.log(reader.result);
        this.inputFile = reader.result;

        let parsed = reader.result.split("\n");

        for(let line in parsed) {
           parsed[line] = parsed[line].split(" ");
        }

        console.log(parsed);

        this.n = parsed[0][0];
        this.capacity = parsed[0][1];

        for(let item in parsed.slice(1, parsed.length)) {
          console.log(parsed[item]);
        }
      };
    }
  }
}
</script>
