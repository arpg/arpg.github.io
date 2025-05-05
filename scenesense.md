---
# Made by Doncey Albin
# Alter as desired. The type references article_v2.html in includes if there are things you want to change.
type: article_v2
title_main: "SceneSense:"
title_follow: "Diffusion models for 3D Occupancy Synthesis from Partial Observation"
# university_name: "University of Colorado - Boulder" # You can comment this out if you dont like it.

author1: "Alec Reed"
author2: "Brendan Crowe"
author3: "Doncey Albin"
author4: "Lorin Achey"
author5: "Bradley Hayes"
author6: "Chris Heckman"

# Links
link_1_url: "https://github.com/arpg/SceneSense"
link_1_color: "yellowgreen"
link_1_text: "GitHub"

link_2_url: "https://arxiv.org/abs/2403.11985"
link_2_color:  "blue"
link_2_text: "ArXiv: SceneSense on Robot"

link_3_url: "https://arxiv.org/abs/2403.11985"
link_3_color:  "red"
link_3_text: "ArXiv: SceneSense"

show_news_updates: True
news_update_1: "2025-05-01 Our paper for applying SceneSense in the real world has been accepted to ICRA 2025! [arxiv link](https://arxiv.org/abs/2409.10681)"
news_update_2: "2024-09-18 Real-world SceneSense applications and model updates on ARXIV: [https://arxiv.org/abs/2409.10681](https://arxiv.org/abs/2409.10681)"
news_update_3: "2024-06-30 SceneSense accepted to IROS 2024!"
---

<!-- CSS for the cube (voxel) container below -->
<style>
    body {
        margin: 0;
        padding: 0;
        position: relative;
        overflow: auto;
    }
    #cube-container {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        z-index: -1;
        perspective: 1000px;
        pointer-events: none; /* Ensure the container doesn't block interaction */
    }
    .cube {
        position: absolute;
        transform-style: preserve-3d;
    }
    .cube-face {
        position: absolute;
        width: 100%;
        height: 100%;
        opacity: 0.8;
        border: 1px solid black; /* Add black border to each face */
    }
</style>

<!-- This is the js script that generates random 3D cubes (voxels) in the background -->
<script>
    // Gen a rand int bw min and max (inclusive)
    function getRandomInt(min, max) {
        return Math.floor(Math.random() * (max - min + 1)) + min;
    }

    // Gen rand color
    function getRandomColor() {
        var colors = ['#FF0000', '#00FF00', '#FFFFFF']; // Red, Green, White, for different occupancies
        return colors[Math.floor(Math.random() * colors.length)];
    }

    // Draw cube at a random position on the sides of the page
    function drawRandomCube() {
        var cube = document.createElement('div');
        cube.classList.add('cube');
        var cubeSize = 20 + 30 * Math.random(); // Random size between 20 and 50px

        // Set cube size and random rotation
        cube.style.width = cubeSize + 'px';
        cube.style.height = cubeSize + 'px';
        cube.style.transform = 'rotateX(' + getRandomInt(-180, 180) + 'deg) rotateY(' + getRandomInt(-180, 180) + 'deg)';

        var cubeColor = getRandomColor();

        // Create cube faces
        var faces = ['front', 'back', 'left', 'right', 'top', 'bottom'];
        faces.forEach(function (face) {
            var faceElement = document.createElement('div');
            faceElement.classList.add('cube-face');
            faceElement.style.backgroundColor = cubeColor;

            switch (face) {
                case 'front':
                    faceElement.style.transform = 'translateZ(' + (cubeSize / 2) + 'px)';
                    break;
                case 'back':
                    faceElement.style.transform = 'rotateY(180deg) translateZ(' + (cubeSize / 2) + 'px)';
                    break;
                case 'left':
                    faceElement.style.transform = 'rotateY(-90deg) translateZ(' + (cubeSize / 2) + 'px)';
                    break;
                case 'right':
                    faceElement.style.transform = 'rotateY(90deg) translateZ(' + (cubeSize / 2) + 'px)';
                    break;
                case 'top':
                    faceElement.style.transform = 'rotateX(90deg) translateZ(' + (cubeSize / 2) + 'px)';
                    break;
                case 'bottom':
                    faceElement.style.transform = 'rotateX(-90deg) translateZ(' + (cubeSize / 2) + 'px)';
                    break;
            }

            cube.appendChild(faceElement);
        });

        // Randomly place the cube on the sides of the window borders
        var side = Math.random() < 0.5 ? 'left' : 'right';
        var x = side === 'left' ? getRandomInt(0, 0.1 * window.innerWidth - cubeSize) : getRandomInt(0.9 * window.innerWidth, window.innerWidth - cubeSize);
        var y = getRandomInt(0, window.innerHeight - cubeSize);

        cube.style.left = x + 'px';
        cube.style.top = y + 'px';

        document.getElementById('cube-container').appendChild(cube);
    }

    // Create cube container
    var cubeContainer = document.createElement('div');
    cubeContainer.id = 'cube-container';
    document.body.appendChild(cubeContainer);

    // Using the function above, draw 10 random 3D cubes on the page
    for (var i = 0; i < 10; i++) {
        drawRandomCube();
    }
</script>

## Presentation Video

<div style="text-align:center;">
  <video width="80%" controls>
    <source src="/video/scenesense/icra_2025_ss.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

<br>

<div style="text-align: center;">
    We present <b>SceneSense</b>, a novel generative 3D diffusion model for synthesizing 3D occupancy information from observations. SceneSense uses a running occupancy map and a single RGB-D camera to generate predicted geometry around the platform, even when the geometry is occluded or out of view. The architecture of our framework ensures that the generative model never overwrites observed free or occupied space, making SceneSense a low risk addition to any robotic planning stack.
</div>

<br>

<div style="overflow: auto; text-align: center;">
    <img src="/img/scenesense/example_results_h1.png" alt="Photo example results" style="display: inline-block; margin-right: 20px;" height="600">
    <img src="/img/scenesense/example_results_h2.png" alt="Photo example results" style="display: inline-block; margin-left: 20px;" height="595">
</div>

<br>

## Method

Our occupancy in-painting method ensures that observed space remains intact while integrating SceneSense predictions. Drawing inspiration from image inpainting techniques like image diffusion and guided image synthesis, our approach continuously incorporates known occupancy information during inference. To execute occupancy in-painting, we select a portion of the occupancy map for diffusion, generating masks for occupied and unoccupied voxels. These masks guide the diffusion process to modify only relevant voxels while introducing noise at each step. This iterative process, depicted below, enhances scene predictions' accuracy while preventing the model from altering observed geometry.

<div style="overflow: auto; text-align: center;">
    <img src="/img/scenesense/framework.png" alt="SceneSense Framework" style="margin-right: auto; margin-left: auto;" height="500">
</div>

<br>

## Presentation Video

<div style="text-align:center;">
  <video width="80%" controls>
    <source src="/video/scenesense/iros_video.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
</div>

<br>

## Citation

```bib
@inproceedings{reed2024scenesense,
  title={SceneSense: Diffusion Models for 3D Occupancy Synthesis from Partial Observation},
  author={Reed, Alec and Crowe, Brendan and Albin, Doncey and Achey, Lorin and Hayes, Bradley and Heckman, Christoffer},
  booktitle={2024 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)},
  pages={7383--7390},
  year={2024},
  organization={IEEE}
}
@article{reed2024online,
  title={Online Diffusion-Based 3D Occupancy Prediction at the Frontier with Probabilistic Map Reconciliation},
  author={Reed, Alec and Achey, Lorin and Crowe, Brendan and Hayes, Bradley and Heckman, Christoffer},
  journal={arXiv preprint arXiv:2409.10681},
  year={2024}
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
