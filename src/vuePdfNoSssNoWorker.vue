<style src="./annotationLayer.css"></style>
<script>
import componentFactory from "./componentFactory.js";

if (process.env.VUE_ENV !== "server") {
  var pdfjsWrapper = require("./pdfjsWrapper").default;
  var PDFJS = require("@fanthos/pdfjs-dist-viewer-legacy");
  var component = componentFactory(pdfjsWrapper(PDFJS));
} else {
  var component = componentFactory({});
}

export default component;
</script>
