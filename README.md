**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Final Project: Point Cloud Registration Using Gaussian Mixure Models**

* SOMANSHU AGARWAL [LinkedIn](https://www.linkedin.com/in/somanshu25)
* SRINATH RAJAGOPALAN [LinkedIn](https://www.linkedin.com/in/srinath-rajagopalan-07a43155)
* DHRUV KARTHIK [LinkedIn](https://www.linkedin.com/in/dhruvkarthik/)

![](https://github.com/somanshu25/CIS565_Final_Project/blob/master/img_gmmreg/GMM_waymo.gif)

### Table of Contents

1. [Introduction](#Introduction)
2. [Gaussian Mixure Models](#Forward-Plus)
3. [Why Probabilistic Models than ICP](#CLustering)
4. [Algorithms](#Effects)
5. [Use Cases](#Optimization)
6. [Performance Analysis](#Analysis)
7. [Future Work](#Future-Work)
8. [Credits](#Credits)

# Introduction

Point cloud registration is greatly used in the field of computer vision applications such as localization. Using detereministic approached such as Iterative Closest point (ICP) works well, but it suffers the issue of coverging to local minima and not aligning the poinclouds properly. One of the ways to improve this limitation is to use probablistic models and learn distributions on the poitn cloud data and align the distributions itself. We are using Gaussian Mixure Model which is driven by expectation maximization algorihtm to learn the distributions on the point cloud data and align them. We will be comparing the CPU and GPU implementation and showcase some of the applications such as unsupervised segmentation and localization. Later on, we will demonstrate a faster approach of GMM model, using Hierarchical Gaussian Mixure Model to learn the distirbutions in logarithmic time. 

# Gaussian Mixure Models

Gaussian Mixure Model (GMM) is the unsupervised probabilistic modelling technique for representing normally distributed subpopulations within an overall population. This is unsupervised as we do not have information about the subpopulations. We estimate the information about subpopulations using Expectation-maximization algorithms. We can apply GMM modelling to both 2D and 3D points to represent the clustering points in the space. The 2D and 3D representations are shown in the figures below.

## Gaussian Mixure Models for 2D Dataset:

Before Clustering            |  After Clustering
:-------------------------:|:-------------------------:
![](img_gmmreg/gmm_before_clustering.png)|  ![](img_gmmreg/gmm_2d.png)

## Gaussian Mixure Modelling for 3D Dataset

The Gaussian Mixure Models are implemented on Stanford Bunny for visualizing GMM in 3D point cloud data. The below two gifs show for 100 and 800 components respectively.

100 Components             |  800 Components
:-------------------------:|:-------------------------:
![](img_gmmreg/bunny_100_Components.gif)| 		![](img_gmmreg/bunny_800_Components.gif)

The performance analysis of CPU and GPU implmentations are shown below:

![](https://github.com/somanshu25/CIS565_Final_Project/blob/master/img_gmmreg/performance_analysis_1.png)
![](https://github.com/somanshu25/CIS565_Final_Project/blob/master/img_gmmreg/performance_analysis_2.png)

The above graphs mention that GPU performance improves with respet to our CPU implementation of point cloud registration.
