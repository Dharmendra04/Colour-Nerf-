# Colour-Nerf-Spherical Harmonics
Using Spherical Harmonics on NeRF 3D reconstruction with a novel NeRF architecture

# Introduction
Link for the Dataset: https://drive.google.com/drive/folders/1kOhYhdmqty8vIGJ2H0j45eKjF0PleebR?usp=sharing

The Neural Radiance Field (NeRF) is revolutionizing computer graphics with its ability to synthesize photorealistic imagery from sparse data. By using artificial neural networks to represent 3D scenes, the NeRF generates stunningly realistic visuals that rival real-world photography. It reconstructs immersive environments from just a few images or viewpoints, bridging the gap between the physical and digital realms. The NeRF is advancing research in computer vision, computer graphics, and augmented reality, with applications in object recognition, scene understanding, and data visualization. As this technology continues to evolve, it promises to unlock new creative possibilities and transform various industries.

# This Repository

This repository contains a NeRF model which used Spherical Harmonics to get the final RGB colour from a novel neural architecture (Which is inspired by Plenoctree [See here](https://alexyu.net/plenoctrees/) but different from their approaches). Additionally I learned about neural radiance field from the following course ([NerF Course Udemy](https://www.udemy.com/course/neural-radiance-fields-nerf/)) and highly reccommend this course for new learners. The fox dataset also obtained from the above course.


<p align="center">
  <img src="https://github.com/Dharmendra04/Colour-Nerf-Spherical-Harmonics/blob/main/Screenshot%202023-06-02%20at%2003.47.01.png">
  <br />
  <em>Figure 1: Nerf Overview and How it works </em>
</p>


# Architecture
The proposed NeRF architecture consists of the following components:

Positional Encoding: The 3D spatial coordinates are encoded using positional encoding with scales ranging from 2^min_deg to 2^(max_deg-1). Instead of computing sine and cosine values separately, we utilize the trigonometric identity cos(x) = sin(x + pi/2) to efficiently compute the encoding.

Evaluation of Points: Given the encoded spatial coordinates and view directions, the model evaluates the points and returns the RGB color and density (sigma) information. The evaluation is performed using a multilayer perceptron (MLP) network.

Ray Creation: Rays are created based on the origin and direction information provided. The rays are discretized into a fixed number of bins (num_bins) to represent the continuous space.

Rendering: The rendering process involves computing the color and density of the points along the rays. The color information is obtained by combining the color predictions from the MLP network with the transmitted light along the rays. The density information is used to compute the alpha (transmittance) values for the points.

Transmittance: The transmittance values are computed using the cumulative product of the alpha values along the rays. This allows for accurate computation of the accumulated transmittance from the camera to each point.


# Conclusion
In this work, we introduced a novel approach to Neural Radiance Fields (NeRF) architecture by incorporating spherical harmonic coordinates to obtain color information. The proposed architecture provides a more efficient and compact representation of the color distribution in 3D space. We hope that this approach will contribute to advancements in 3D scene synthesis and rendering techniques.

Please refer to the code for more details and parameter settings. Feel free to experiment with different configurations and datasets to explore the capabilities of the proposed NeRF architecture.

Please also note that the results shown in the notebooks are only trained for 20 epochs, due to the resitriction of training time in google colab by training for more epochs like 1000, we can get more an more the clear image same as the raw image. See the change of image clarity with number of epochs here. [Tiny NeRF](https://github.com/bmild/nerf/blob/master/tiny_nerf.ipynb). 

