---
title: 'Accelerated Container Image'
date: 2022-03-02 00:00:00
tags:
- containerd
- container image
---

### Overview
`Accelerated Container Image` is a sub-project of containerd. It is a core technology of Alibaba and was published at [DADI: Block-Level Image Service for Agile and Elastic Application Deployment. USENIX ATC'20]("https://www.usenix.org/conference/atc20/presentation/li-huiba"). `Accelerated Container Image` was opened at Mar 2011 and became a containerd sub-project at Nov 2011.

At the heart of the acceleration is overlaybd, which is a new remote image format based on block device. It is used for image acceleration by supporting fetching image data on-demand without downloading and unpacking the whole image before a container running. With overlaybd image format, we can cold start a container instantly.

[Accelerated Container Image](https://github.com/containerd/accelerated-container-image) contains the containerd snapshotter and conversion tools for overlaybd images.

`Overlaybd` is the name of our image format, which is a block-device based image format. The [overlaybd](https://github.com/containerd/overlaybd) repository containes the storage backend of `Accelerated Container Image`, provides a merged view of a sequence of block-based layers as an block device.

### Block-based image

The existing lazy pulling image formats are filesystem-based. However, implementing a POSIX-complaint file system interface and exposing it via the OS kernel is complex. And underlay filesystem support is restricted in current file-system-based image services.

Overlaybd provides a virtual block device for container image to support lazy-pulling image which has fully posix-compliant and multiple filesystem supported as a supplement.

Several features show as below:

- High Performance

  It's a block-device-based storage of OCI image, which has much lower complexity than filesystem-based implementations. For example, cross-layer hardlink and non-copy commands like chown are very complex for filesystem-based image without copying up, but is natively supported by overlaybd. Overlaybd outperforms filesystem-based solutions in performance.

- High Reliability

  Overlaybd outputs virtual block devices through TCMU(TCM in userspace), which is widely used and supported in most operation systems. Overlaybd backstore can recover from failures or crashes, which is difficult for FUSE-based image formats.

- Security

  Block-based solution has small attack surface.

- Efficiency virtualization supported

  Passing a block-device from host to microVM (like kata-container) via virtio-blk is usually less performance cost. On the other hand, passing 'rootfs' from host to microVM via virtio-fs is also supported after overlaybd has been mounted.

- Native Support for Writable

  Overlaybd can be used as a writable/container layer. The end-users can build their overlaybd images naturally without conversion.

- Multiple File System Supported

  Overlaybd is independent of the underlay filesystem. It's convenient for users to choose their ideal image filesystem, such as xfs, btrfs, zfs even NTFS, and makes it possible to run Windows container on Linux host, or vice versa.
