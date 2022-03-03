---
title: DADI - Data Accelerator for Disaggregated Infrastructure
position: 0
header_title: D A D I
subtitle: |-
  <strong>D</strong>ata <strong>A</strong>ccelerator for <br> <strong>D</strong>isaggregated <strong>I</strong>nfrastructure

color: lighter-gray
button:
  title: Get started
  url: https://data-accelerator.github.io
extended_header: true

features:

- title:
  handle: intro
  background: yellow
  width: wide
  subsections:
  - title: '<span style="font-size: 18px">Accelerated container image</span>'
    body: Sub-project of containerd, contains a containerd snapshotter and image conversion tools. <a class="text_link" href="(blog/Accelerated_container_image/)">more</a>
    image: "/assets/containerd.png"
    button:
      title: Github
      url: https://github.com/containerd/accelerated-container-image
  - title: Overlaybd
    body: Sub-project of containerd, contains the backend storage service of overlaybd image format.
    image: "/assets/overlaybd.png"
    button:
      title: Github
      url: https://github.com/containerd/overlaybd
  - title: Buildkit
    body: Based on moby/buildkit, easily and directly build and export overlaybd images.
    image: "/assets/build.png"
    button:
      title: Github
      url: https://github.com/data-accelerator/buildkit
  - title: P2P data distribution
    body: Use p2p protocol to speed up HTTP file download for registry in large-scale clusters.
    image: "/assets/p2p2.001.png"
    button:
      title: Github
      url: https://github.com/data-accelerator/dadi-p2proxy

- title: About DADI
  handle: develop
  background: darkest-gray
  width: wide
  subsections:
  - title: Introduction
    body: |-
      DADI is short for Data Accelerator for Disaggregated Infrastructure. DADI provides a solution for data acceleration which is typically used for container images acceleration, and can be easily expand into other scenarios.

      The whole approach of accelerated image service is published at [DADI: Block-Level Image Service for Agile and Elastic Application Deployment. USENIX ATC'20]("https://www.usenix.org/conference/atc20/presentation/li-huiba")

      DADI has been widely used in Alibaba and Alibaba Cloud and already been integrated by Alibaba Cloud Registry (ACR), Function Compute and other serverless services.
    image: "/assets/dadi.jpg"
    color: red
  - title: Key Features
    body: |-
      <strong>High Performace</strong>
      Block-device-based image format has much lower complexity than filesystem-based implementations. For example, cross-layer hardlink and non-copy commands like chown are very complex for filesystem-based image without copying up, but is natively supported by overlaybd.

      <strong>High Reliability</strong>
      Overlaybd outputs virtual block devices through [TCMU](https://www.kernel.org/doc/Documentation/target/tcmu-design.txt), which is a linux kernel module and widely supported in most operation systems. Overlaybd backstore can recover from failures or crashes, which is difficult for FUSE-based image formats.
    image: "/assets/perf.png"
    color: purple

- title: Core Technology
  handle: manage
  width: wide
  color: blue
  subsections:
  - title: Overlaybd
    handle: collaborate
    body: Overlaybd is a block level container image format, providing a merged view of block-based layers.
    image: "/assets/overlaybd-big.png"
  - title: Zfile
    handle: preview
    body: Zfile is a compression file format supporting online decompression, which can reduce storage and transmission costs.
    image: "/assets/zfile.png"
  - title: P2P
    handle: edit
    body: Uses P2P protocol to speed up HTTP file download not only for container images.
    image: "/assets/pp.png"


layout: index
---

