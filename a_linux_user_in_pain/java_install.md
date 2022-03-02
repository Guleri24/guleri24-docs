---
title: Java setup with PATH - GraalVM
parent: A Linux User In Pain
has_children: false
nav_order: 3
---
Date: 4 Mar 2022

# GraalVM setup on Fedora
1. Download the version you want from [GraalVM Releases repository on GitHub
](https://github.com/graalvm/graalvm-ce-builds/releases). Remember to choose  the architecture correctly but i'm assuming most of you have AMD64.
2. Untar the .tar.gz file
	**`tar -xzf graalvm-ce-java<version>-linux-amd64-<version>.tar.gz`**
3. mv the file **`/usr/lib/jvm/`** directory
	**`mv graalvm-ce-java<version>-linux-amd64-<version> /usr/lib/jvm`**
4. Now edit the** `/etc/profile`** file and add the following to the last.
	**`export JAVA_HOME=/usr/lib/jvm/graalvm-ce-java17-22.0.0.2 `**
	**`export PATH=$JAVA_HOME/bin:$PATH`**
5. For it is better to logout or restart to get system wide changes but we can also use 
	**`source /etc/profile`** 
	to see the system wide changes but did'nt works always.
