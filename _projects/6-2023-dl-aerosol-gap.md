---
title: "Deep Learning for Filling Aerosol Data Gaps"
excerpt: "A ConvLSTM model to fill aerosol data gaps hampered by clouds.<br/><img src='/figures/projects/2023-dl-aerosol-1.png' width=500>"
collection: projects
---

I am currently working on a project to fill missing aerosol data using a ConvLSTM model. I am collaborating with [Dr. Yi Wang](https://www.linkedin.com/in/yi-wang-tamu/) on this project. This work will be presenting at the [2024 American Meteorological Society Annual Meeting](https://annual.ametsoc.org/index.cfm/2024/) in Baltimore, Maryland. The project is still in progress. The following is a brief introduction to the project.

AMS annual meeting abstract
===========================

Aerosol optical depth (AOD) serves as a critical observable for atmospheric particles, significantly informing our understanding of climate change, radiation balance, and air quality dynamics. Satellite imaging is the predominant method for large-scale AOD analysis. However, the acquisition of comprehensive AOD datasets is often hampered by clouds in these images, resulting in notable data gaps. 
 
Deep learning, particularly the use of multi-layered neural networks, offers a promising avenue because of its ability to discern complex, nonlinear relationships in large datasets. As part of NOAA’s Earth Observation Digital Twin (EO-DT) prototype effort, we employ Convolutional Long Short-Term Memory (ConvLSTM) networks to predict and fill the AOD data gaps from the GOES-18 Advanced Baseline Imager (ABI). The model is trained using clear-sky AOD observations, capturing both spatial and temporal variations. To further optimize our reconstructions, we fuse our dataset with high-resolution AOD readings from the Visible Infrared Imaging Radiometer Suite (VIIRS). This synergy improves the model's accuracy, facilitating granular and spatially consistent AOD predictions. We compare our results with classical techniques such as back-filling of cloud-obscured retrievals with previous observations. Our approach suggests that combining deep learning with multi-source data fusion can provide valuable insights, potentially addressing some persistent challenges in AOD data acquisition.

Preliminary results
===================

![ConvLSTM aerosol prediction](/figures/projects/2023-dl-aerosol-1.png)
<p style="text-align: center;">This figure depicts the aerosol optical depth (AOD) at various time steps. In our ConvLSTM model, we utilize six frames as input and six frames as output. The first row represents the input data, the second row displays the ground truth, and the third row shows the model's predictions.</p>
