---
ID: 1428
post_title: >
  How to install Ubuntu Server 18.04 on
  Raspberry Pi 3 without the external
  peripherals
author: admin
post_excerpt: ""
layout: post
permalink: >
  https://coding-banana.com/how-to-install-ubuntu-server-18-04-on-raspberry-pi-3/
published: true
post_date: 2018-12-16 22:52:36
---
<ul>
<li><span style="font-weight: 400;">Raspberry PI as an Ubuntu Classic server</span></li>
</ul>
<p></p>
<p><span style="font-weight: 400;">SOURCES: </span></p>
<p><span style="font-weight: 400;">- https://medium.com/a-swift-misadventure/how-to-setup-your-raspberry-pi-2-3-with-ubuntu-16-04-without-cables-headlessly-9e3eaad32c01</span></p>
<p><span style="font-weight: 400;">- https://ubuntu-pi-flavour-maker.org/download/</span></p>
<p><span style="font-weight: 400;">- https://askubuntu.com/questions/775597/how-to-use-onboard-wifi-on-raspberry-pi-3-with-ubuntu-server-16-04</span></p>
<p><span style="font-weight: 400;">- https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-04-bionic-beaver-linux</span></p>
<p></p>
<p><span style="font-weight: 400;">Commands: </span></p>
<p></p>
<p><span style="font-weight: 400;">1) download the image</span></p>
<p><span style="font-weight: 400;">wget https://www.finnie.org/software/raspberrypi/ubuntu-rpi3/ubuntu-18.04-preinstalled-server-armhf+raspi3.img.xz</span></p>
<p></p>
<p><span style="font-weight: 400;">2) install the image to SD card</span></p>
<p><span style="font-weight: 400;">sudo apt-get install gddrescue</span></p>
<p><span style="font-weight: 400;">unxz ubuntu-18.04-preinstalled-server-armhf+raspi3.img.xz</span></p>
<p><span style="font-weight: 400;">sudo ddrescue -d -D --force ubuntu-18.04-preinstalled-server-armhf+raspi3.img /dev/sdx</span></p>
<p><span style="font-weight: 400;"># use lsblk command to see the device name, mine was /dev/sdb</span></p>
<p></p>
<p><span style="font-weight: 400;">3) Put SD card in Raspberry, connect power and ethernet and connect via SSH</span></p>
<p><span style="font-weight: 400;">ssh ubuntu@&lt;IP_of_your_PI&gt;</span></p>
<p><span style="font-weight: 400;">&gt; password: ubuntu</span></p>
<p><span style="font-weight: 400;"># change default password immediately </span></p>
<p></p>
<p><span style="font-weight: 400;">4) Update and Upgrade system to latest version</span></p>
<p><span style="font-weight: 400;">sudo apt-get update &amp;&amp; sudo apt-get upgrade &amp;&amp; sudo apt-get dist-upgrade &amp;&amp; sudo do-release-upgrade -d</span></p>
<p><span style="font-weight: 400;"># watch out for prompts, especially for ssh, sshd, or something in regards to SSH -&gt; do not get locked out of your account</span></p>
<p></p>
<p><span style="font-weight: 400;">5) Set static IP address</span></p>
<p><span style="font-weight: 400;">TBD</span></p>
<p><span style="font-weight: 400;"># do port forwarding on your router too - use the static IP address you just defined, and forward port 22</span></p>
<p><span style="font-weight: 400;"># check IP addresses on your router</span></p>
<p><span style="font-weight: 400;"># make a dyn dns (noip, for example)</span></p>
<p></p>
<p><span style="font-weight: 400;">6) Install useful tools</span></p>
<p><span style="font-weight: 400;">sudo apt-get install htop</span></p>
<p><span style="font-weight: 400;"># TBD</span></p>
<p></p>
<p><span style="font-weight: 400;">7) Use WiFi card (internal)</span></p>
<p><span style="font-weight: 400;">sudo apt-get install wireless-tools wpasupplicant</span></p>
<p><span style="font-weight: 400;">sudo reboot</span></p>
<p><span style="font-weight: 400;"># now reconnect via SSH</span></p>
<p></p>

<!-- wp:heading -->
<h2>Rationale? Why would you do that?</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Because, why not? :D<br></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Raspberry Pi is definitely not a device you want to use as a server. It is designed for <g class="gr_ gr_152 gr-alert gr_gramm gr_inline_cards gr_run_anim Grammar only-ins doubleReplace replaceWithoutSep" id="152" data-gr-id="152">completely</g> different purpose(s). However, installing an Ubuntu Server on it is possible and it is fun. However, due to its hardware limitations and processor architecture do not expect much out of it.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Prerequisites</h2>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>I would personally recommend to have the following prerequisites:&nbsp;</p>
<!-- /wp:paragraph -->

<!-- wp:list -->
<ul><li>Raspberry Pi 3 (obviously)</li><li>fast SD card (at least class 10 and at least 16 GB)</li><li>computer (preferably running Linux; I will not cover Mac and Windows)&nbsp;</li><li>Ethernet cable</li><li>Internet access (over Ethernet)</li></ul>
<!-- /wp:list -->

<!-- wp:paragraph -->
<p>I would really recommend internet over Ethernet for starters. It will make your life easier. Later on, you may set up the Wi-Fi.</p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Also, you may set up your Wi-Fi immediately using an external peripherals (monitor and mouse). However, these instructions are intended for the set-up without any peripherals. You will only connect to your Raspberry Pi server over SSH.</p>
<!-- /wp:paragraph -->

<!-- wp:heading -->
<h2>Preparing the SD card</h2>
<!-- /wp:heading -->

<!-- wp:heading {"level":3} -->
<h3>Format your SD card</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Before you start, make sure your SD card is properly formatted. I would recommend FAT 32 file system. This will be reformatted anyways...</p>
<!-- /wp:paragraph -->

<!-- wp:heading {"level":3} -->
<h3>Download the Linux Ubuntu Server image</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Just visit this link: <a href="https://www.finnie.org/software/raspberrypi/ubuntu-rpi3/ubuntu-18.04-preinstalled-server-armhf+raspi3.img.xz ">https://www.finnie.org/software/raspberrypi/ubuntu-rpi3/ubuntu-18.04-preinstalled-server-armhf+raspi3.img.xz </a></p>
<!-- /wp:paragraph -->

<!-- wp:paragraph -->
<p>Alternatively, you can enter this command in your terminal: </p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<pre lang="sh">
wget https://www.finnie.org/software/raspberrypi/ubuntu-rpi3/ubuntu-18.04-preinstalled-server-armhf+raspi3.img.xz
</pre>
<!-- /wp:html -->

<!-- wp:heading {"level":3} -->
<h3>Installing the image on SD card</h3>
<!-- /wp:heading -->

<!-- wp:paragraph -->
<p>Run this command to install adequate tools to your machine:</p>
<!-- /wp:paragraph -->

<!-- wp:html -->
<pre lang="sh">
sudo apt-get install gddrescue
</pre>
<pre lang="sh">
unxz ubuntu-18.04-preinstalled-server-armhf+raspi3.img.xz
</pre>
<pre lang="sh">
sudo ddrescue -d -D --force ubuntu-18.04-preinstalled-server-armhf+raspi3.img /dev/sdx
</pre>
# use lsblk command to see the device name, mine was /dev/sdb
<!-- /wp:html -->