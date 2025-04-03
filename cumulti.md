---
# Made by Doncey Albin
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "CU-Multi:"
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

<!-- css for javascript to animate Huntie rotating about -->
<style>
    body {
        margin: 0;
        padding: 0;
        overflow: auto;
        position: relative;
    }
    #huntie-image-container {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
        pointer-events: none;
    }
    .robot-img {
        position: absolute;
        width: 100px;
        height: auto;
        user-select: none;
        transition: transform 1s ease-in-out, left 3s ease-in-out, top 3s ease-in-out;
    }
</style>

<div id="huntie-image-container"></div>

<script>
    // robot colors
    const glowColors = ['limegreen', 'purple', 'orange', 'deepskyblue'];

    function getRandomInt(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
    }

    function checkOverlap(x, y, size, positions) {
        for (let pos of positions) {
            if (Math.abs(x - pos.x) < size && Math.abs(y - pos.y) < size) {
                return true;
            }
        }
        return false;
    }

    function scatterImagesOnSides(src, numImages, size) {
        const container = document.getElementById('huntie-image-container');
        const positions = [];
        const allImgs = [];

        for (let i = 0; i < numImages; i++) {
            let x, y, attempts = 0;
            const side = Math.random() < 0.5 ? 'left' : 'right';
            do {
                x = side === 'left' ? getRandomInt(0, 0.1 * window.innerWidth - size) : getRandomInt(0.9 * window.innerWidth, window.innerWidth - size);
                y = getRandomInt(0, window.innerHeight - size);
                attempts++;
            } while (checkOverlap(x, y, size, positions) && attempts < 100);

            positions.push({x, y});

            const img = document.createElement('img');
            img.src = src;
            img.classList.add('robot-img');
            // add 
            if (i < glowColors.length) {
                img.style.filter = `drop-shadow(0 0 4px ${glowColors[i]})`;
            }
            img.style.left = x + 'px';
            img.style.top = y + 'px';
            img.dataset.angle = getRandomInt(0, 360);

            container.appendChild(img);
            allImgs.push(img);
        }

        for (const img of allImgs) {
            animateImage(img, allImgs, size);
        }
    }

    function animateImage(img, allImgs, size) {
        setInterval(() => {
            // rotate mr huntie
            const angleChange = getRandomInt(-90, 90);
            img.dataset.angle = parseFloat(img.dataset.angle) + angleChange;
            img.style.transform = `rotate(${img.dataset.angle}deg)`;

            // translate mr huntie along new heading
            setTimeout(() => {
                const distance = getRandomInt(20, 50);
                const rad = img.dataset.angle * (Math.PI / 180);
                const moveX = Math.cos(rad) * distance;
                const moveY = Math.sin(rad) * distance;

                const newX = parseFloat(img.style.left) + moveX;
                const newY = parseFloat(img.style.top) + moveY;

                let overlap = false;
                for (const other of allImgs) {
                    if (other === img) continue;
                    const otherX = parseFloat(other.style.left);
                    const otherY = parseFloat(other.style.top);
                    if (Math.abs(newX - otherX) < size && Math.abs(newY - otherY) < size) {
                        overlap = true;
                        break;
                    }
                }

                // make sure robots are not colliding...
                if (!overlap) {
                    img.style.left = newX + 'px';
                    img.style.top = newY + 'px';
                }
            }, 3000);
        }, 3000);
    }

    // 4 images of Huntie with 60px on each on sides of the page :)
    scatterImagesOnSides('/img/cumulti/huntie_bev.png', 4, 60);
</script>

<div style="text-align: justify; background-color:rgb(225, 225, 225); padding: 5px; border-radius: 5px;">
  <div style="text-align:center; font-size: 36px;">
    <strong>Abstract</strong>
  </div>

  <p style="text-align: justify; flex: 1; padding: 10px;">
    Multi-robot systems (MRSs) are valuable for tasks such as search and rescue due to their ability to coordinate over shared observations. A central challenge in these systems is aligning independently collected perception data across space and time– i.e., multi-robot data association. While recent advances in collaborative SLAM (C-SLAM), map merging, and inter-robot loop closure detection have significantly progressed the field, evaluation strategies still predominantly rely on splitting a single trajectory from single-robot SLAM datasets into multiple segments to simulate multiple robots. Without careful consideration to how a single trajectory is split, this approach will fail to capture realistic pose-dependent variation in observations of a scene inherent to multi-robot systems. To address this gap, we present CU-Multi, a multi-robot dataset collected over multiple days at two locations on the University of Colorado Boulder campus. Using a single robotic platform, we generate four synchronized runs with aligned start times and deliberate percentages of trajectory overlap. CU-Multi includes RGB-D, GPS with accurate geospatial heading, and semantically annotated LiDAR data. By introducing controlled variations in trajectory overlap and dense lidar annotations, CU-Multi offers a compelling alternative for evaluating methods in multi-robot data association.
  </p>
</div>

## System and Sensors


<div style="display: flex; margin-bottom: 20px; background-color:rgba(255, 255, 255, 0.90);">
  <div style="display: flex; flex-direction: column; align-items: center; margin-right: 15px;">
      <img src="/img/cumulti/huntie_sensors.png" alt="" style="margin-bottom: 10px;" width="400">
  </div>

  <p style="text-align: justify; flex: 1;">
      We collected the CU-Multi Dataset in Boulder, Colorado at the CU Boulder campus. The CU-Multi dataset was collected using the AgileX Hunter SE platform modified with a custom-designed electronics housing (see Figure 2). Inside the housing, the system includes an Intel NUC i7 with 16 GB of RAM, a power distribution board, an Ouster interface module, and a 217 Wh battery. Externally, a mounting plate on the rear of the Hunter SE accommodates two u-blox ANN-MB-00 GNSS antennas, while a front-mounted plate holds a 64-beam Ouster LiDAR sensor, a RealSense D455 RGB-D camera, a Lord MicroStrain G7 IMU, and a Lord RTK cellular modem with an external antenna.
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
      CU-Multi was collected in two areas on the CU campus. The first environment covers CU's Main Campus (main_campus), which is a dense academic setting with structured paths, buildings, and pedestrian areas. The total trajectory length for all robots on the Main Campus span approximately 7.4 kilometers (see below for individual robot trajectory lengths). The second environment, Kittredge Loop (kittredge_loop), is a more open and varied outdoor region south of the main campus. This area features less constrained terrain, dynamic objects, many parked vehicles, and contributes an additional 9.3 kilometers of trajectory data.

      Each environment includes four robot runs with deliberate trajectory overlap, enabling evaluation of multi-robot SLAM methods under varying levels of observational redundancy. All runs are synchronized to begin at a shared rendezvous point, and end within 4 meters of one another, supporting fine-grained inter-robot data association tasks.
  </p>
</div>


### Main Campus Environment (*main_campus*)

<div style="display: flex; background-color:rgba(255, 255, 255, 0.76); margin-bottom: 20px;">
  <!-- <div style="display: flex; flex-direction: column; align-items: center; margin-left: 15px; margin-right: 15px;">
      <img src="/img/cumulti/main_image.png" alt="" width="300">
  </div> -->

  <div style="display: flex; justify-content: center;">
    <div>
      <table style="border-collapse: collapse; border: 2px solid black;">
        <tr>
          <th style="border: 1px solid black; padding: 8px;">Environment</th>
          <th style="border: 1px solid black; padding: 8px;">Robot ID</th>
          <th style="border: 1px solid black; padding: 8px;">Total Path Length</th>
        </tr>
        <tr>
          <td style="border: 1px solid black; padding: 8px;" rowspan="4">Main Campus</td>
          <td style="border: 1px solid black; padding: 8px;">robot1</td>
          <td style="border: 1px solid black; padding: 8px;">1295.96 m</td>
        </tr>
        <tr>
          <td style="border: 1px solid black; padding: 8px;">robot2</td>
          <td style="border: 1px solid black; padding: 8px;">1360.43 m</td>
        </tr>
        <tr>
          <td style="border: 1px solid black; padding: 8px;">robot3</td>
          <td style="border: 1px solid black; padding: 8px;">1816.76 m</td>
        </tr>
        <tr>
          <td style="border: 1px solid black; padding: 8px;">robot4</td>
          <td style="border: 1px solid black; padding: 8px;">2971.38 m</td>
        </tr>
      </table>
      <!-- <p style="text-align: center;"><strong>Table 2.</strong> <em>Table of individual trajectory lengths for Main Campus and Kittredge Loop environments.</em></p> -->
    </div>
  </div>
</div>

### Kittredge Loop Environment (*kittredge_loop*)

<div style="display: flex; background-color:rgba(255, 255, 255, 0.76); margin-bottom: 20px;">
  <!-- <div style="display: flex; flex-direction: column; align-items: center; margin-left: 15px; margin-right: 15px;">
      <img src="/img/cumulti/main_image.png" alt="" width="300">
  </div> -->

  <div style="display: flex; justify-content: center;">
    <div>
      <table style="border-collapse: collapse; border: 2px solid black;">
        <tr>
          <th style="border: 1px solid black; padding: 8px;">Environment</th>
          <th style="border: 1px solid black; padding: 8px;">Robot ID</th>
          <th style="border: 1px solid black; padding: 8px;">Total Path Length</th>
        </tr>
        <tr>
          <td style="border: 1px solid black; padding: 8px;" rowspan="4">Kittredge Loop</td>
          <td style="border: 1px solid black; padding: 8px;">robot1</td>
          <td style="border: 1px solid black; padding: 8px;">1136.41 m</td>
        </tr>
        <tr>
          <td style="border: 1px solid black; padding: 8px;">robot2</td>
          <td style="border: 1px solid black; padding: 8px;">1373.37 m</td>
        </tr>
        <tr>
          <td style="border: 1px solid black; padding: 8px;">robot3</td>
          <td style="border: 1px solid black; padding: 8px;">2792.06 m</td>
        </tr>
        <tr>
          <td style="border: 1px solid black; padding: 8px;">robot4</td>
          <td style="border: 1px solid black; padding: 8px;">4005.75 m</td>
        </tr>
      </table>
      <!-- <p style="text-align: center;"><strong>Table 2.</strong> <em>Table of individual trajectory lengths for Main Campus and Kittredge Loop environments.</em></p> -->
    </div>
  </div>
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
@inproceedings{albin2025cumulti,
  title={CU-Multi: A Dataset for Multi-Robot Data Association},
  author={Albin, Doncey and Mena, Miles and Thomas, Annika and Biggie, Harel and Sun, Xuefei and Woods, Dusty and McGuire, Steve and Heckman, Christoffer},
  booktitle={arXiv preprint arXiv:####.#####},
  year={2025}
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
