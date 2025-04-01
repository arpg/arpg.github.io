---
# Made by Doncey Albin
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "CU-Multi"
title_follow: "A Dataset for Multi-Robot Data Association"
# university_name: "University of Colorado - Boulder" # You can comment this out if you dont like it.

author1: "Doncey Albin"
author2: "Miles Mena"
author3: "Annika Thomas"
author4: "Harel Biggie"
author5: "Xuefei Sun"
author6: "Dusty Woods"
author7: "Steve McGuire"
author8: "Christoffer Heckman"

# Links at bottom. Removing '<linkname>_link' below will remove from page.
link_1_url: "https://github.com/arpg/CU-Multi"
link_1_color: "yellowgreen"
link_1_text: "GitHub"

# link_2_url: ""
# link_2_color:  "blue"
# link_2_text: "ArXiv"

link_3_url: "https://drive.google.com/drive/u/1/folders/1lrhCDy2flNDyyPkKeTmA8tNgFj4JxSwi"
link_3_color:  "red"
link_3_text: "Download Dataset"

# talk_link: "https://google.com"
# talk_link_color: "red"
# talk_link_text: "IROS Talk"

# media_coverage_link:
# media_coverage_link_color:
# media_coverage_link_text: "Media Coverage"

# bibtex_link: "https://google.com"
# bibtex_link_color: "purple"
# bibtex_link_text: "BiTex"

show_news_updates: False
news_update_1: "2024-12-25 Dataset visualization code now available."
---

<div style="text-align: center;">
  Multi-robot systems (MRSs) are valuable for tasks such as search and rescue due to their ability to coordinate over shared observations. A central challenge in these systems is aligning independently collected perception data across space and time– i.e., multi-robot data association. While recent advances in collaborative SLAM (C-SLAM), map merging, and inter-robot loop closure detection have significantly progressed the field, evaluation strategies still predominantly rely on splitting a single trajectory from single-robot SLAM datasets into multiple segments to simulate multiple robots. Without careful consideration to how a single trajectory is split, this approach will fail to capture realistic pose-dependent variation in observations of a scene inherent to multi-robot systems. To address this gap, we present CU-Multi, a multi-robot dataset collected over multiple days at two locations on the University of Colorado Boulder campus. Using a single robotic platform, we generate four synchronized runs with aligned start times and deliberate percentages of trajectory overlap. CU-Multi includes RGB-D, GPS with accurate geospatial heading, and semantically annotated LiDAR data. By introducing controlled variations in trajectory overlap and dense lidar annotations, CU-Multi offers a compelling alternative for evaluating methods in multi-robot data association.
</div>

## Dataset

<div style="display: flex; margin-bottom: 20px;">
  
  <!-- Left side: two stacked images -->
  <div style="display: flex; flex-direction: column; align-items: center; margin-right: 15px;">
      <img src="/img/cumulti/huntie_sensors.png" alt="" style="margin-bottom: 10px;" width="400">
      <img src="/img/cumulti/main_image.png" alt="" width="400">
  </div>

  <!-- Right side: justified text -->
  <p style="text-align: justify; flex: 1;">
      We collected the CU-Multi Dataset in Boulder, Colorado at the CU Boulder campus. The CU-Multi dataset was collected using the AgileX Hunter SE platform modified with a custom-designed electronics housing (see Figure 2). Inside the housing, the system includes an Intel NUC i7 with 16 GB of RAM, a power distribution board, an Ouster interface module, and a 217 Wh battery. Externally, a mounting plate on the rear of the Hunter SE accommodates two u-blox ANN-MB-00 GNSS antennas, while a front-mounted plate holds a 64-beam Ouster LiDAR sensor, a RealSense D455 RGB-D camera, a Lord MicroStrain G7 IMU, and a Lord RTK cellular modem with an external antenna.
  </p>
</div>


<!-- <div style="text-align: center; margin-top: 20px;">
    <img src="/img/cumulti/main_image.png" alt="" style="display: inline-block; margin: 0 10px;" height="600">
    <img src="/img/cumulti/KL_lidar_overlay_trans.png" alt="" style="display: inline-block; margin: 0 10px;" height="600">
</div> -->


<!-- ## Presentation Video -->

<!-- <div style="text-align:center;">
  <video width="80%" controls>
    <source src="/video/scenesense/iros_video.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div> -->

<!-- <br>

## Citation

```bibtex
@article{Harlow2024ARXIV, 
   title   = {ColoRadar+: An extension of the dense millimeter-wave radar dataset ColoRadar}, 
   author  = {Kyle Harlow, Doncey Albin, Kristen Such, Miles Mena, Dusty Woods, Anna Zavei-Boroda, Christoffer Heckman}, 
   journal = {arXiv preprint arXiv:####.#####},
   year    = {2025}, 
}
``` -->

<!-- For styling above Bibtex -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.19.0/themes/prism-okaidia.min.css"
      integrity="sha512-pGi87NmT0VeSbmZBK40y3wF4H2DlpCYc5lrO/3F/RPhnwn262NReW3jFtG2iZWhbpoWT5MDzBzawpOri+jcUTw==" crossorigin="anonymous" />

<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.19.0/prism.min.js"
        integrity="sha512-9ndS8HgVHWQq2A/kpIxygbIZQ7oljc9/AvoEv8SQDy192nAuCGSdk7OdAfCZLDkbRJLZMsrV0NXycMSLLNTWCw==" crossorigin="anonymous">
</script>

<script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.19.0/plugins/autolinker/prism-autolinker.min.js"
        integrity="sha512-/uypNVmpEQdCQLYz3mq7J2HPBpHkkg23FV4i7/WSUyEuTJrWJ2uZ3gXx1IBPUyB3qbIAY+AODbanXLkIar0NBQ==" crossorigin="anonymous">
</script>

<script src="https://cdn.jsdelivr.net/npm/prismjs-bibtex@2.1.0/prism-bibtex.js"
        integrity="sha256-A5GMUmGHpY8mVpfcaRLQFeHtmdjZLumKBOMpf81FXX0="
        crossorigin="anonymous" referrerpolicy="no-referrer">
</script>
