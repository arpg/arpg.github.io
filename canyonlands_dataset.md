---
# Made by Doncey Albin
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "The Canyonlands Dataset"
title_follow: ""
# university_name: "University of Colorado - Boulder" # You can comment this out if you dont like it.

author1: "Kristen Such"
author2: "Miles Mena"
author3: "Christoffer Heckman"

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

<div style="text-align: justify; background-color:rgb(225, 225, 225); padding: 5px; border-radius: 5px;">
  <div style="text-align:center; font-size: 36px;">
    <strong>Abstract</strong>
  </div>

  <p style="text-align: justify; flex: 1; padding: 10px;">
    Abstract here.
  </p>
</div>

## System and Sensors


<div style="display: flex; margin-bottom: 20px; background-color:rgba(255, 255, 255, 0.90);">
  <div style="display: flex; flex-direction: column; align-items: center; margin-right: 15px;">
      <img src="/img/cumulti/huntie_sensors.png" alt="" style="margin-bottom: 10px;" width="400">
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

## Environments

<div style="display: flex; background-color:rgba(255, 255, 255, 0.76); margin-bottom: 20px;">
  <div style="display: flex; flex-direction: column; align-items: center; margin-left: 15px; margin-right: 15px;">
      <img src="/img/cumulti/main_image.png" alt="" width="300">
  </div>

  <p style="text-align: justify; flex: 1;">
      We collected the CU-Multi Dataset in Boulder, Colorado at the CU Boulder campus. The CU-Multi dataset was collected using the AgileX Hunter SE platform modified with a custom-designed electronics housing (see Figure 2). Inside the housing, the system includes an Intel NUC i7 with 16 GB of RAM, a power distribution board, an Ouster interface module, and a 217 Wh battery. Externally, a mounting plate on the rear of the Hunter SE accommodates two u-blox ANN-MB-00 GNSS antennas, while a front-mounted plate holds a 64-beam Ouster LiDAR sensor, a RealSense D455 RGB-D camera, a Lord MicroStrain G7 IMU, and a Lord RTK cellular modem with an external antenna.
  </p>
</div>
      
### Main Campus Environment (*main_campus*)

### Kittredge Loop Environment (*kittredge_loop*)

<!-- <div style="display: flex; justify-content: center;">
  <div>
    <table style="border-collapse: collapse; border: 2px solid black;">
      <tr>
        <th style="border: 1px solid black; padding: 8px;">Environment</th>
        <th style="border: 1px solid black; padding: 8px;">Robot ID</th>
        <th style="border: 1px solid black; padding: 8px;">Total Path Length</th>
        <th style="border: 1px solid black; padding: 8px;"># Intra-robot loop closures</th>
        <th style="border: 1px solid black; padding: 8px;"># Inter-robot loop closures</th>
      </tr>
      <tr>
        <td style="border: 1px solid black; padding: 8px;" rowspan="4">Kittredge Loop</td>
        <td style="border: 1px solid black; padding: 8px;">robot1</td>
        <td style="border: 1px solid black; padding: 8px;">1136.41 m</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
      </tr>
      <tr>
        <td style="border: 1px solid black; padding: 8px;">robot2</td>
        <td style="border: 1px solid black; padding: 8px;">1373.37 m</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
      </tr>
      <tr>
        <td style="border: 1px solid black; padding: 8px;">robot3</td>
        <td style="border: 1px solid black; padding: 8px;">2792.06 m</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
      </tr>
      <tr>
        <td style="border: 1px solid black; padding: 8px;">robot4</td>
        <td style="border: 1px solid black; padding: 8px;">4005.75 m</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
      </tr>
      <tr>
        <td style="border: 1px solid black; padding: 8px;" rowspan="4">Main Campus</td>
        <td style="border: 1px solid black; padding: 8px;">robot1</td>
        <td style="border: 1px solid black; padding: 8px;">1295.96 m</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
      </tr>
      <tr>
        <td style="border: 1px solid black; padding: 8px;">robot2</td>
        <td style="border: 1px solid black; padding: 8px;">1360.43 m</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
      </tr>
      <tr>
        <td style="border: 1px solid black; padding: 8px;">robot3</td>
        <td style="border: 1px solid black; padding: 8px;">1816.76 m</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
      </tr>
      <tr>
        <td style="border: 1px solid black; padding: 8px;">robot4</td>
        <td style="border: 1px solid black; padding: 8px;">2971.38 m</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
        <td style="border: 1px solid black; padding: 8px;">-</td>
      </tr>
    </table>
    <p style="text-align: center;"><strong>Table 1.</strong> <em>Table of intra-robot loop closures in different environments</em></p>
  </div>
</div> -->

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
