# linux-notebook
#this file cantain my problem and answer 
1. how fix my wifi stable
You can find the firmware download for your device hardware here with instructions on how to install it here. In your case, as was mine, I downloaded the firmware for Intel® Centrino® Wireless-N 1000. NOTE: the link provided is for kernel versions 3.2+. If memory serves correctly that should work for 13.04 but to be sure run the command: uname -a. As per the instructions perform the following after downloading the firmware:

$ tar -xvzf iwlwifi-1000-ucode-39.31.5.1.tgz 
$ cd iwlwifi-1000-ucode-39.31.5.1/
$ sudo cp iwlwifi-1000-5.ucode /lib/firmware/
That's it! As I stated this has worked so far. If the issue manifests itself again I will modify or delete this answer, but for mine and everyone with this problem I hope this is a permanent fix.
