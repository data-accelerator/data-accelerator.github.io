---
title: 'Accelerated Container Image'
date: 2022-03-02 00:00:00
tags:
- containerd
- container image
---

`Accelerated Container Image` is a sub-project of containerd. It is a core technology of Alibaba and was published at [DADI: Block-Level Image Service for Agile and Elastic Application Deployment. USENIX ATC'20]("https://www.usenix.org/conference/atc20/presentation/li-huiba"). `Accelerated Container Image` was opened at Mar 2011 and became a containerd sub-project at Nov 2011.

At the heart of the acceleration is overlaybd, which is a new remote image format based on block device. It is used for image acceleration by supporting fetching image data on-demand without downloading and unpacking the whole image before a container running. With overlaybd image format, we can cold start a container instantly.

[Accelerated Container Image](https://github.com/containerd/accelerated-container-image) contains the containerd snapshotter and conversion tools for overlaybd images.

`Overlaybd` is the name of our image format, which is a block-device based image format. The [overlaybd](https://github.com/containerd/overlaybd) repository containes the storage backend of `Accelerated Container Image`, provides a merged view of a sequence of block-based layers as an block device.



