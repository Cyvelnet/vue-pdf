<style src="./annotationLayer.css"></style>
<script>
import componentFactory from "./componentFactory.js";

import pdfjsWorker from "@fanthos/pdfjs-dist-viewer-legacy/build/pdf.worker.js";

if (process.env.VUE_ENV !== "server") {
  var pdfjsWrapper = require("./pdfjsWrapper").default;
  var PDFJS = require("@fanthos/pdfjs-dist-viewer-legacy");

  if (
    typeof window !== "undefined" &&
    "Worker" in window &&
    navigator.appVersion.indexOf("MSIE 10") === -1
  ) {
    PDFJS.GlobalWorkerOptions.workerSrc = pdfjsWorker;
  }

  var component = componentFactory(pdfjsWrapper(PDFJS));
} else {
  var component = componentFactory({});
}

export default component;
</script>
