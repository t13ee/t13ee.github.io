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
