---
# Made by Doncey Albin
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "ColoRadar+:"
title_follow: "An extension of the dense millimeter-wave radar dataset ColoRadar"
# university_name: "University of Colorado - Boulder" # You can comment this out if you dont like it.

author1: "Kyle Harlow"
author2: "Doncey Albin"
author3: "Kristen Such"
author4: "Miles Mena"
author5: "Dusty Woods"
author6: "Anna Zavei-Boroda"
author7: "Christoffer Heckman"

# Links at bottom. Removing '<linkname>_link' below will remove from page.
github_link: "https://github.com/arpg/ColoRadarPlus"
github_link_color: "yellowgreen"
github_link_text: "GitHub"

arxiv_link: "https://github.com/arpg/ColoRadarPlus"
arxiv_link_color: "blue"
arxiv_link_text: "ArXiv"

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

show_news_updates: False
news_update_1: "2024-12-25 Dataset visualization code now available."
---


<div style="text-align: center;">
    Millimeter-Wave (mmWave) Radar has become a compelling alternative sensor for odometry and mapping in visually degraded environments due to the longer-wavelength’s ability to bypass particles which interrupt visual and near-visual sensors. 
    However, the low resolutions, especially in angular dimensions, and sparse nature of many mmWave radars make accurate odometry difficult. In order to promote continued research in this area, we present ColoRadar+. Coloradar+ is an extension of the ColoRadar Dataset which includes improved ground truth odometry, and RGB-D camera data not included in the original dataset. We also propose a data-driven radar-inertial odometry network, which leverages a dense radar image front-end to compensate for some of the perceived drawbacks of mmWave radar. We train and test this network on a new mmWave radar dataset, <b>ColoradarPlus</b>.
</div>

## Dataset

<div style="text-align: left; margin-bottom: 20px;">
  If you would like to download the ColoRadar+ Dataset or specific runs from environments, you can do so here: <a href="https://example.com" style="color:blue;">(DOWNLOAD)</a>
</div>

<div style="text-align: justify;">
    <!-- <img src="/img/coloradarplus/radar_rig.png" alt="Photo example results" style="display: inline-block; margin-right: 20px;" height="300"> -->
    <img src="/img/coloradarplus/radar_rig.png" alt="Photo example results" style="float: left; margin-right: 10px;" height="250">
    We collected the ColoradarPlus dataset across a diverse set of urban environments, in and around the University of Colorado - Boulder campus. We maintained recording in the indoor building environments of the Intelligent Robotics Laboratory (IRL), and Engineering Center Hallways (EC). We also capture outdoor data within the Engineering Center Courtyard (courtyard), and a fast-moving collection along Boulder Creek Path and across the University of Colorado- Boulder Campus, where the sensor-rig was attached to the back of an electrical bicycle (ebike). Lastly we collect data in two different parking garages the Center For Community parking garage (C4C), an underground parking lot with solid concrete walls and Regent Parking Garage (regent), an above ground parking lot with multiple levels. Each of these environments are detailed below.
</div>

<br>

<div style="overflow: auto; text-align: center;">
    <img src="/img/coloradarplus/example_image.png" alt="Photo example results" style="display: inline-block; margin-right: 20px;" height="600">
</div>

## DeepRIO

We create a fusion architecture, DeepRIO, similar to Chen et al. (2019); Lu et al. (2020) which employs a first-of-its-kind dense 3D convolutional encoder network styled similarly to Wang et al. (2017) between two radar-images and a 6DoF inertial network Silva do Monte Lima et al. (2019) to track odometry.

<div style="overflow: auto; text-align: center;">
    <img src="/img/coloradarplus/network_architecture.png" alt="DeepRIO Framework" style="margin-right: auto; margin-left: auto;" height="500">
</div>

<br>

## Presentation Video

<!-- <div style="text-align:center;">
  <video width="80%" controls>
    <source src="/video/scenesense/iros_video.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div> -->

<br>

## Citation

```bibtex
@article{Harlow2024ARXIV, 
   title   = {ColoRadar+: An extension of the dense millimeter-wave radar dataset ColoRadar}, 
   author  = {Kyle Harlow, Doncey Albin, Kristen Such, Miles Mena, Dusty Woods, Anna Zavei-Boroda, Christoffer Heckman}, 
   journal = {arXiv preprint arXiv:####.#####},
   year    = {2025}, 
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
