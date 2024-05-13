# ![#f03c15](https://github.com/moggieuk/Happy-Hare/blob/main/doc/f03c15.png) ![#c5f015](https://github.com/moggieuk/Happy-Hare/blob/main/doc/c5f015.png) ![#1589F0](https://github.com/moggieuk/Happy-Hare/blob/main/doc/1589F0.png) Software Installation

This section deals with installing Happy Hare to the host computer (most commonly the Raspberry Pi).

## Software Installation Steps
Let's install the software now.
Basically, the installation proceeds as with any other git based software, indeed like Klipper itsself.

### Cloning into Happy Hare
The first step is to clone the Happy Hare repository onto your Raspberry Pi. If you're unfamiliar with cloning, it just copies all the data in the git repository to your local computer. Since the Happy Hare git has all the necessay software, we use the `git clone` functionality to pull everything from github to the local computer (the rpi, in most cases of Klipper). So, go ahead and log into your rpi via ssh.

In power shell, and with Mainsail, this will look like this:  
```ssh pi@mainsailos.local```  

 - *You will notice in the following pictures the bash prompt is `pi@brokkr:~`. Yours won't look like that. It will be `pi@<hostname.:~` where the hostname is likely "mainsailos" or the ip address. No need to worry. I have more than one printer running Klipper, so I had to change the name to keep them separate.*

Alternatively, you can use your Klipper ip address, which will look something like this:  
```ssh pi@192.168.0.256```  
(You'll need to change the ip address.)  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/834e3a13-6b8f-47a4-ae5a-5e4da6716bbf" />
</p>

From there, you're going to clone Happy Hare software to your rpi:  
```
cd ~
git clone https://github.com/moggieuk/Happy-Hare.git
```  
(it's ok to click the copy icon and right click in the ssh terminal to paste or just type it out if you want.)  
Let that finish. It should only take a few seconds, and you'll now have your very own copy of Happy Hare stored on your rpi!
<p align="center">
  <img src="https://www.icegif.com/wp-content/uploads/2023/07/icegif-431.gif" alt="YESSS" width="110" height="102" />
</p>

Now, you're going to change to the Happy Hare directory using the `cd` command (`cd` is Linux Geek for "change directory"):  
```cd Happy-Hare```  

Here is a picture of the previous steps successfully performed:
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/4bd059da-4da3-4b44-9e39-52f87c7aad2c" alt="Successful Steps" width="700" height="347" />
</p>

### Running the installation script
Finally, you'll install Happy Hare using a bash script which contains all the commands necessary to install Happy Hare:  
```./install.sh -i```  

 - *Here, we're using the `-i` switch (switch is more Linux Geek for "option") to activate an interactive install. This will help guide you through setting most basic options for your MMU. This is generally only needed for the first install. Upgrading can be done by `./install.sh` with no switches.*   

You'll be asked a series of questions pertaining to your hardware and options.
#### 1.  MMU Type
Choose from the list. The options will from here out based on what you choose:   

* ERCF v1.1
    - "stock" ERCF v1.1 (Threaded rods, support blocks between every 3rd gate, etc.) 
* ERCF V2.0
    - This includes the "ThumperBlocs" mod. However, you'll need the "Thicker" ThumperBlocks.
* Tradrack v1.0  
* Other  
    - Custom setup
    - Just basic files you can edit yourself later.  

<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/8bb01bc4-13fa-4a47-a45b-0f52184ecce4" alt="Initial setup 1" width="700" height="347" /></p>  

For this example, we're just going to run through a ERCF V2.O install, as that is the most popular option at the time of this writing.  

#### 2. Filament Blocks
You'll be asked if you're using Thumperblocks.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/7f842c87-0a08-48d1-b5d1-7421fd7e089e" alt="Initial setip 2 - ThumperBlocks" width="810" height="35" />
</p>
Enter the appropriate answer.  

#### 3. Number of Gates
Happy Hare installer then asks for the number of gates.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/32644faf-6c52-4c4b-91f6-63e1db27e512" alt="Initial setup 3 - gates" width="319" height="34" />
</p>
Enter the correct number of gates for your ERCF.  

#### 4. Control Board
Select the type of control board you have installed.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/de6ff395-9785-4c5d-9fed-92a48cd119d2" alt="Initial setup 4 - Board Type" width="364" height="131" />
</p>

#### 5. Control Board Address
Happy Hare will then attempt to figure out where your control board is. So far, this doesn't work for CANBUS boards.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/57814902-26cf-47d4-ada7-bee5f2c0eb41" />
</p>  

#### 6.  Selector Touch Operation
Decide whether or not to enable Selector Touch operation. This can help with recovery of an error, but is also a bit difficult to get set up properly. It's better to say "no" and get it working after you're more familiar with the ERCF and Happy Hare.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/17309aee-2980-4184-bc70-9eeca3399aba" />
</p>  

#### 7. LED Options
If you have neopixels installed on your ERCF, enable them here.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/91053e99-1bf6-4ebd-9a75-e2aac326390b" />
</p>

#### 8. Servo Options
Select your servo option from the list.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/f26d3fd0-0fe7-4d11-9f2e-fb66ce02a11c" />
</p>

#### 9.  Clog detection
If you have a reliable encoder, it's probably best to enable clog detection and set it to automatic. This acts like a smart filament sensor and will pause the print if something goes bad with the filament feed.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/2b0228c4-91cc-4797-b0a7-99ba64c40b16" />
</p>  

#### 10.  Tool to gate mapping  
Happy Hare has the capability to map multiple gates to one tool. This allows for "endless spool" operation. When one spool runs out, if you have the same material and color mapped to another gate, it will automatically switch to the other gate and resume printing. If you have an encoder and gate switches, this option is recommended for long prints.
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/25dfd408-1fab-4136-809f-88d6174b18aa" />
</p>

#### 11. Final step
The last step asks to add the `[include mmu*]` lines to your printer.cfg. ***On initial setup, select yes.*** In the image below, it was set to "no" because Happy Hare is already installed and wasn't needed.  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/27418658-2433-4338-ab9d-38cd7037980d" />
</p>

From here, Happy Hare will install itself with the options you've selected. You should have a nice little report that Happy Hare is ready:  
<p align="center">
  <img src="https://github.com/IRTrail/Happy-Hare/assets/53546870/f3adbaab-618a-4948-9470-b50a7105411b" />
</p>

Now, you have Happy Hare installed on your rpi. Feels good, doesn't it?  
<p align="center">
  <img src="https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fmedia.giphy.com%2Fmedia%2FOHS0O0rLKg9vq%2Fgiphy.gif&f=1&nofb=1&ipt=b54551ebf58b81ed62210f2070778e0c1ed17aa85a443f2f960eed73283c38b2&ipo=images" />
</p>