---
layout: post
title: picoCTF 2024 Writeup
date: 2024-03-29 20:48 +0700
categories: [picoCTF, CTF, writeup]
tags: [ctf, reverse engineering, binary exploitation, writeup]
img_path: "/assets/picoCTF"
image:
  path: logo.png
---

Hello everyone, picoCTF recently held a challenge from March 12 to March 26, 2024. Here are some of the problems that I have solved.

Let's get started!

# Reverse Engineering

## packer (100pts)

![packer image picoCTF](/img/20240329220649.png)

The challenge strongly hints (it's in the binary name, challenge name, and is a literal hint) that this is a binary packed with UPX. Additionally, running `strings out | grep upx` will display `$Info: This file is packed with the UPX executable packer http://upx.sf.net $`.

![shell image](/img/20240329223902.png)

UPX is a free, portable, extendable, high-performance executable packer for several executable formats.

We can download the latest release of UPX from the [GitHub releases page](https://github.com/upx/upx/releases). Extracting the archive gives us a folder with a `upx` binary. We can run `./<folder-name>/upx -d out` to decompress the binary and replace it on disk. Now, our `out` file is unpacked.

![shell image](/img/20240329225456.png)

After completing the above tasks, the job now is to reverse engineer the `out` file using [Ghidra](https://ghidra-sre.org/) or [IDA](https://hex-rays.com/ida-pro/). When analyzing the pseudocode, I discovered this line `Password correct, please see flag: 7069636f4354467b5539585f556e5034636b314e365f42316e345269 33535f65313930633366337d`

![ghidra image](/img/20240329232511.png)

Our final task is to [convert hexadecimal to ASCII](https://www.rapidtables.com/convert/number/hex-to-ascii.html).

`FLAG: picoCTF{U9X_UnP4ck1N6_B1n4Ri3S_e190c3f3}`
