---
type: article
title:  "SUNSPOT Dataset"
---

We introduce a new dataset, SUN-Spot, for localizing objects using spatial referring expressions (REs). SUN-Spot is the only RE dataset which uses RGB-D images. It also contains a greater average number of spatial prepositions and more cluttered scenes than previous RE datasets. Using a simple baseline, we show that including a depth channel in RE models can improve performance on both generation and comprehension.

## Paper

[![Preview of Pages 1 and 2](/img/sunspot_paper.png) Download the paper here.](/papers/PID6091773.pdf)

### Citation 

C.  Mauceri,  M.  Palmer,  and  C.  Heckman,  “SUN-Spot:  An  RGB-D  Dataset  With  Spatial  Referring
Expressions,” in
_International Conference on Computer Vision Workshop on Closing the Loop Between
Vision and Language_
, 2019.


{% raw %}
```
@inproceedings{Mauceri2019,
author = {Mauceri, Cecilia and Palmer, Martha and Heckman, Christoffer},
booktitle = {International Conference on Computer Vision Workshop on Closing the Loop Between Vision and Language},
title = {{SUN-Spot: An RGB-D Dataset With Spatial Referring Expressions}},
year = {2019}
}
```
{% endraw %}

## Downloads

- [SUNRGBD Images](http://rgbd.cs.princeton.edu/) 
- SUN-Spot Annotations
    - [refs(boulder).p](https://zenodo.org/records/14693339/files/refs(boulder).p?download=1) - The referring expressions
    - [instances.json](https://zenodo.org/records/14693339/files/instances.json?download=1) - The SUNRGBD annotations in COCO format
    - [vocab.txt](https://zenodo.org/records/14693339/files/vocab.txt?download=1) - The vocabulary
- [Code Repository](https://github.com/crmauceri/ReferringExpressions)

## Examples

To provide a taste of the images and annotations in SUN-Spot, here are 10 randomly selected objects from the dataset with all of their referring expressions.

{::options parse_block_html="true" /}
<div class="container">

{% for object in site.data.sunspot_visualization %}
<div class="row">

<div class="col-sm-4">
![{{object.object}}]({{object.url}}){:height="300px"} 
</div>

<div class="col-sm-8">
{% for refexp in object.refexps %}
- {{refexp}}
{% endfor %}
</div>

</div>
{% endfor %}

</div>



