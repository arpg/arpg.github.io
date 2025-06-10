---
# Made by Doncey Albin
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "The Canyonlands Dataset"
title_follow: ""
# university_name: "University of Colorado - Boulder" # You can comment this out if you dont like it.

author1: "Kristen Such"
author2: "Doncey Albin"
author3: "Christoffer Heckman"

# Links at bottom. Removing '<linkname>_link' below will remove from page.
link_1_url: "https://github.com/suchkristenwow/CanyonlandsDataset"
link_1_color: "yellowgreen"
link_1_text: "GitHub"

# link_2_url: ""
# link_2_color:  "blue"
# link_2_text: "ArXiv"

link_3_url: "https://drive.google.com/drive/folders/1W5xcQVJETsYlKwovsj7DfAhi3iAook8n?usp=sharing"
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

<div style="text-align: justify; background-color:rgb(225, 225, 225); padding: 5px; border-radius: 5px;">
  <div style="text-align:center; font-size: 36px;">
    <strong>Abstract</strong>
  </div>
  <p style="text-align: justify; flex: 1; padding: 10px;">
    Rangelands provide many ecological services including livestock forage, water retention and carbon sequestration
    making their health integral for soil health and air quality. However, restoration efforts of degraded rangelands have
    seen little success in recent years. It is thought that subtle ecological features, called microsites, are critical for plant
    growth outcomes. Autonomous robots offer a solution to indentify and intervene based off these subtle features, but the
    lack of relevant data in these environments is a limiting factor to getting highly granular, multi-seasonal data necessary
    for testing ecological hypotheses. In this paper, we introduce the Canyonlands Dataset, a large-scale, multi-modal
    dataset collected near to Canyonlands National Park in Southeastern Utah using an autonomous ground vehicle. The
    dataset includes high-resolution camera imagery, RTK-GPS trajectories, 3D lidar point clouds, and ground-truth vehicle
    odometry. To support reproducibility and foster research in autonomous environmental monitoring and restoration, we
    provide detailed documentation, calibration files, and code for dataset interaction.
  </p>
</div>


## System and Sensors

<div style="display: flex; margin-bottom: 20px; background-color:rgba(255, 255, 255, 0.90);">
  <div style="display: flex; flex-direction: column; align-items: center; margin-right: 15px;">
      <img src="/img/canyonlands_dataset/main.png" alt="" style="margin-bottom: 10px;" width="700">
  </div>

  <p style="text-align: justify; flex: 1;">
    The Canyonlands dataset was collected in Canyonlands National Park in Utah, USA. We collected the dataset using a Clearpath Husky platform equiped with a Ouster lidar,  
  </p>
</div>

<div style="display: flex; justify-content: center; background-color:rgba(255, 255, 255, 0.90);">
  <div>
    <table style="border-collapse: collapse; border: 2px solid black;">
      <tr>
        <th style="border: 1px solid black; padding: 8px;">Equipment</th>
        <th style="border: 1px solid black; padding: 8px;">Model Name</th>
        <th style="border: 1px solid black; padding: 8px;">Characteristics</th>
        <th style="border: 1px solid black; padding: 8px;">Resolution</th>
        <th style="border: 1px solid black; padding: 8px;">FoV</th>
        <th style="border: 1px solid black; padding: 8px;">Sensor Rate</th>
      </tr>
      <tr>
        <th style="border: 1px solid black; padding: 8px;"> LiDAR </th>
        <td style="border: 1px solid black; padding: 8px;"> Ouster OS-64 </td>
        <td style="border: 1px solid black; padding: 8px;"> 200 m range </td>
        <td style="border: 1px solid black; padding: 8px;"> 64v x 1028h </td>
        <td style="border: 1px solid black; padding: 8px;"> 45° x 360° </td>
        <td style="border: 1px solid black; padding: 8px;"> 20 Hz </td>
      </tr>
      <tr>
        <th style="border: 1px solid black; padding: 8px;"> RGB-D Camera </th>
        <td style="border: 1px solid black; padding: 8px;"> Intel Realsense D455 </td>
        <td style="border: 1px solid black; padding: 8px;"> RGB: Global Shutter </td>
        <td style="border: 1px solid black; padding: 8px;"> 1280 × 800 </td>
        <td style="border: 1px solid black; padding: 8px;">90° x 65° </td>
        <td style="border: 1px solid black; padding: 8px;"> 30 Hz </td>
      </tr>
      <tr>
        <th style="border: 1px solid black; padding: 8px;"> IMU</th>
        <td style="border: 1px solid black; padding: 8px;"> MicroStrain 3DM-GQ7-GNSS/INS </td>
        <td style="border: 1px solid black; padding: 8px;"> ±8 g </td>
        <td style="border: 1px solid black; padding: 8px;"> 300 dps </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
        <td style="border: 1px solid black; padding: 8px;"> 400 Hz </td>
      </tr>
      <tr>
        <th style="border: 1px solid black; padding: 8px;"> Network Interface Modem </th>
        <td style="border: 1px solid black; padding: 8px;"> MicroStrain 3DM-RTK Modem </td>
        <td style="border: 1px solid black; padding: 8px;"> 2 cm, 0.1° accuracy </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
        <td style="border: 1px solid black; padding: 8px;"> 2 Hz </td>
      </tr>
      <tr>
        <th style="border: 1px solid black; padding: 8px;"> GNSS Antennas </th>
        <td style="border: 1px solid black; padding: 8px;"> u-blox ANN-MB-00 </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
      </tr>
      <tr>
        <th style="border: 1px solid black; padding: 8px;"> Main Computer </th>
        <td style="border: 1px solid black; padding: 8px;"> Intel NUC </td>
        <td style="border: 1px solid black; padding: 8px;"> Intel i7 CPU @ 3.20GHz, 16GB RAM </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
        <td style="border: 1px solid black; padding: 8px;"> - </td>
      </tr>
    </table>
    <p style="text-align: center;"><strong>Table 1.</strong> <em>Hardware Specifications.</em></p>
  </div>
</div>

## Seasons

<div style="display: flex; background-color:rgba(255, 255, 255, 0.76); margin-bottom: 20px;">
  <div style="display: flex; flex-direction: column; align-items: center; margin-left: 15px; margin-right: 15px;">
      <img src="/img/canyonlands_dataset/seasons.png" alt="" width="700">
  </div>

  <p style="text-align: justify; flex: 1;">
      The Canyonlands dataset is broken into to separate data collection times: in November 2022 and May 2023.
  </p>
</div>

<!-- ## Citation
```bibtex
@article{Harlow2024ARXIV, 
   title   = {ColoRadar+: An extension of the dense millimeter-wave radar dataset ColoRadar}, 
   author  = {Kyle Harlow, Doncey Albin, Kristen Such, Miles Mena, Dusty Woods, Anna Zavei-Boroda, Christoffer Heckman}, 
   journal = {arXiv preprint arXiv:####.#####},
   year    = {2025}, 
} -->

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