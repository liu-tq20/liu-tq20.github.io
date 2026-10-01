---
layout: page
permalink: /adaptive-patience/
title: "Adaptive Patience: Modeling Human Help Needs for Proactive AI Intervention Timing"
description: "Tian-Qi Liu*, Diyu Zou*, Saleh Kalantari. Submitted to CHI 2027. Preprint preview (first 3 pages)."
nav: false
---

<!-- Preprint preview: renders only the first few pages of the PDF via PDF.js -->
<div id="pdf-preview-pages" style="max-width: 850px; margin: 0 auto;">
  <p style="text-align: center;">Loading preview…</p>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js"></script>
<script>
  (function () {
    var pdfUrl = "/assets/img/preprint_pdf/Adaptive%20Patience_Proactive%20Agent.pdf";
    var maxPages = 3;
    var container = document.getElementById("pdf-preview-pages");
    window.pdfjsLib.GlobalWorkerOptions.workerSrc = "https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js";
    window.pdfjsLib
      .getDocument(pdfUrl)
      .promise.then(function (pdf) {
        container.innerHTML = "";
        var n = Math.min(maxPages, pdf.numPages);
        var chain = Promise.resolve();
        for (var i = 1; i <= n; i++) {
          (function (pageNum) {
            chain = chain.then(function () {
              return pdf.getPage(pageNum).then(function (page) {
                var viewport = page.getViewport({ scale: 2 });
                var canvas = document.createElement("canvas");
                canvas.width = viewport.width;
                canvas.height = viewport.height;
                canvas.style.cssText = "width: 100%; display: block; margin-bottom: 16px; border-radius: 4px; background: #fff;";
                canvas.className = "z-depth-1";
                container.appendChild(canvas);
                return page.render({ canvasContext: canvas.getContext("2d"), viewport: viewport }).promise;
              });
            });
          })(i);
        }
        return chain.then(function () {
          var note = document.createElement("p");
          note.style.cssText = "text-align: center; font-size: 0.9rem; opacity: 0.7;";
          note.textContent = "Preview limited to the first " + n + " pages. Talk to me if you are interested in this work!";
          container.appendChild(note);
        });
      })
      .catch(function () {
        container.innerHTML = '<p style="text-align: center;">Failed to load preview.</p>';
      });
  })();
</script>
