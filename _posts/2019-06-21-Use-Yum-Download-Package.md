---
layout: wiki
title: Use Yum Down Package
categories: [linux]
description: use yum down ...
keywords: centos, redhat, yum, down
---
## Use Yum Download Package

### 1. install `yum-utils`

```bash
yum -y install yum-utils 
```

### 2. download package 

#### 1. download package without dependencies

```bash
yumdownloader packageName 
```
E.g.
```bash
yumdownloader vim
```

#### 2. download package with dependencies
```bash
yum -y install packageName --downloadonly --downloaddir=/save/path 
```
E.g.
```bash
yum -y install vim --downloadonly --dwonloaddir=./
```
if the package was installed, nothing download.

#### 3. download package from cdrom yum repo
```bash
yum --downloadonly -y install packageName | grep "will be installed" | xargs -d '\n' printf "expr '%s' : '.*Package \(.*\) [0-9].*'\n" | bash | xargs -d '\n' yumdownloader
```
E.g.
```bash
yum --downloadonly -y install vim | grep "will be installed" | xargs -d '\n' printf "expr '%s' : '.*Package \(.*\) [0-9].*'\n" | bash | xargs -d '\n' yumdownloader
```