---
layout: single
title: "Curriculum Vitae"
permalink: /cv/
author_profile: false
---

<a class="btn btn--primary" href="/files/Mehta_Vibhuti_CV.pdf" target="_blank" rel="noopener">Open CV (PDF)</a>

<div class="cv-embed">
<iframe src="/files/Mehta_Vibhuti_CV.pdf#navpanes=0&view=FitH&toolbar=1" width="100%" height="1100px" style="border: none;" title="Vibhuti Mehta CV"></iframe>
</div>

<div id="cv-mobile" class="cv-mobile"></div>

<script>
(function () {
  if (window.matchMedia('(min-width: 769px)').matches) return;
  var container = document.getElementById('cv-mobile');
  var s = document.createElement('script');
  s.src = 'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.min.js';
  s.onload = function () {
    pdfjsLib.GlobalWorkerOptions.workerSrc =
      'https://cdnjs.cloudflare.com/ajax/libs/pdf.js/3.11.174/pdf.worker.min.js';
    pdfjsLib.getDocument('/files/Mehta_Vibhuti_CV.pdf').promise.then(function (pdf) {
      var width = container.clientWidth;
      var dpr = window.devicePixelRatio || 1;
      function render(n) {
        if (n > pdf.numPages) return;
        pdf.getPage(n).then(function (page) {
          var scale = width / page.getViewport({ scale: 1 }).width;
          var vp = page.getViewport({ scale: scale * dpr });
          var canvas = document.createElement('canvas');
          canvas.width = vp.width;
          canvas.height = vp.height;
          canvas.style.width = '100%';
          container.appendChild(canvas);
          page.render({ canvasContext: canvas.getContext('2d'), viewport: vp })
            .promise.then(function () { render(n + 1); });
        });
      }
      render(1);
    }).catch(function () {
      container.innerHTML = '<p>The CV could not be displayed here. Please use the button above.</p>';
    });
  };
  document.head.appendChild(s);
})();
</script>
