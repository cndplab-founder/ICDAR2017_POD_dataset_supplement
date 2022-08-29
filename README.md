
# ICDAR2017_POD_dataset_supplement

This repository contains a great supplement to the ICDAR2017 POD dataset in terms of table structure recognition, from <strong>Prof. Cheng-Lin Liu's Group, Institute of Automation, Chinese Academy of Sciences</strong> [1]. 

Thank Cheng-Lin Liu's Group for their helpful contributions!

## Overview

The original ICDAR2017 POD dataset is composed of the specific page objects(e.g. tables, formulas, figures(including charts)) in document images, and this dataset is extracted and relabeled based on the table ones.

The following table shows the number of training and test images, which are fully annotated.

|    |  TrainSet | TestSet |
|--- |   :----:  | :----:  | 
|Total   | 549 | 243 |


## Annotation Format

```
<?xml version="1.0" encoding="UTF-8"?>
<document filename="POD_0393.jpg">
    <table>
        <Coords points="164,142 896,142 896,396 164,396"/>
        ...
        <cell id="1" neighbors="0:R 2:R 4:L 5:L">
            <Coords points="392,202 889,202 889,339 392,339"/>
        </cell>
       ...
       <cell id="4" neighbors="1:R 3:B 5:T 12:L">
            <Coords points="292,289 325,289 325,310 292,310"/>
       </cell>
       ...
       <cell id="13" neighbors="3:R 12:T">
           <Coords points="173,350 246,350 246,386 173,386"/>
       </cell>
    </table>
</document>
```
For the annotation of dataset, The notation is modified from ICDAR 2019 cTDaR Competition format, appending `<cell/id>` and `<cell/neighbors>` to store the relations between the adjoining cells.

In the XML file, Each `<table>` element corresponds to a table, which contains a single `<Coords>` element with `[points]` attribute to indicates the coordinates of the bounding polygon with 4 vertices. Table contain a list of `<cell>` elements.

Especially in this format, each `<cell>` element has a attribute `[id]` which denotes a unique numerical index for this cell, and a attribute `[neighbors]`, which denotes its left, right, top, bottom adjoining cell id by `[L]`,`[R]`,`[T]`,`[B]` separately. The number of adjoining cells in each direction is unfixed, such as 0, 1, 2, etc. 


## Reference
[1] Xiao-Hui Li, Fei Yin, Cheng-Lin Liu. Table Structure Recognition and Form Parsing by End-to-End Object Detection and Relation Parsing. Pattern Recognition.
