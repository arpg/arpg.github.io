---
# Made by Doncey Albin
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "RMap:"
title_follow: "Millimeter-Wave Radar Mapping Through Volumetric Upsampling"
# university_name: "University of Colorado - Boulder" # You can comment this out if you dont like it.

author1: "Ajay N. Mopidevi"
author2: "Kyle Harlow"
author3: "Chris Heckman"

# Links
link_1_url: "https://github.com/arpg/RMap"
link_1_color: "yellowgreen"
link_1_text: "GitHub"

link_2_url: "https://arxiv.org/abs/2310.13188"
link_2_color:  "blue"
link_2_text: "ArXiv"


# summary_video_link:
# summary_video_link_color:
# summary_video_link_text: "Summary Video Link"

# talk_link: "https://google.com"
# talk_link_color: "red"
# talk_link_text: "IROS Talk"

# media_coverage_link:
# media_coverage_link_color:
# media_coverage_link_text: "Media Coverage"

# bibtex_link: "https://google.com"
# bibtex_link_color: "purple"
# bibtex_link_text: "BiTex"
---

<div style="text-align: center;">
    Millimeter Wave Radar is being adopted as a viable alternative to lidar and radar in adverse visually degraded conditions, such as in the presence of fog and dust. However, this sensor modality suffers from severe sparsity and noise under nominal conditions, which makes it difficult to use in precise applications such as mapping. This work presents a novel solution to generate accurate 3D maps from sparse radar point clouds. <b>RMap</b> uses a generative transformer architecture which upsamples, denoises, and fills the incomplete radar maps to resemble lidar maps. We test this method on the ColoRadar dataset to demonstrate its efficacy. 
</div>

<br>

<div style="overflow: auto; text-align: center;">
    <img src="/img/rmap/RMapOverview.png" alt="Photo example results" style="display: inline-block; margin-right: auto;" height="300">
    <img src="/img/rmap/Results.png" alt="Photo example results" style="display: inline-block; margin-left: auto;" height="300">
</div>

<br>

## Method

An (A) automotive-grade system-on-chip mmWave radar sensor produces (B) Radar point clouds generated by CFAR thresholding along a trajectory (C). A (D) Radar Map is generated using the radar point clouds with Radar Octomap along the trajectory of the robot, with different pose locations highlighted. This map is then divided into (E) Patches of size 2048 sampled at different locations along the trajectory. These patches are passed through the pointcloud completion network, AdaPoinTr, to produce (F) predicted map patches. The predicted point clouds of size 8192 from AdaPoinTr are then merged into (G) the final predicted radar map.

<div style="overflow: auto; text-align: center;">
    <img src="/img/rmap/SystemDiagram.png" alt="RMap System Diagram" style="margin-right: auto; margin-left: auto;" height="250">
</div>

<br>

## Presentation Video

<div style="text-align:center;">
  <video width="80%" controls>
    <source src="/video/rmap/rmap_iros_submisson_video.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

<br>

## Citation

```bib
@article{mopidevi2023rmap,
  title={RMap: Millimeter-Wave Radar Mapping Through Volumetric Upsampling},
  author={Mopidevi, Ajay Narasimha and Harlow, Kyle and Heckman, Christoffer},
  journal={arXiv preprint arXiv:2310.13188},
  year={2023}
}
```

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