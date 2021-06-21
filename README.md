# Custom_Rom
Hello, guys if you are here it means you want to learn How To Build Any Custom Rom For Your Android Phone or Compile Rom From Source. So finely I am back with a great guide for everyone. In that guide, I will teach you how you can Build Any Custom Rom For Your Android Phone without pc. Yes, you can build without pc. We will use our great smartphone to Build Any Custom Rom For Your Android Phone. So guys if you want to Compile Rom From Source then you will need to follow step by step guide. So without wasting time let’s get started.

## What is an Android Custom ROM :
Android ROM is to a phone’s firmware, based on Google’s Android platform. Android is open source and that’s why any developer can edit the source code, recompile it, and re-release for a wide variety of devices. Users can install ROMs to change a device’s look and behaviour. All Custom ROMs are developed by the Android community, mostly a group of core developers who do this purely out of a passion for modding. This means that most are absolutely free. Custom ROMs are available for Android phones, tablets, media players, smartwatches and almost any type of device which is running Android.

When you buy your Android phone, it comes with a “stock ROM” or the “stock firmware”. This is to the preinstalled version of the operating system. This ROM has limited functionality as defined by the phone’s manufacturer. By flashing a custom ROM, you can unlock extra functionality and sometimes improve the performance.

### Requirements To Compile Rom From Source :
We are working on our Android device, so you need to full fill all the requirements.

### (1) Ubuntu 16.04 Server (VM):
You will need Ubuntu 16.04 Server to build custom ROMs. Because I am using Ubuntu 16.04 Server every time. You will get servers from AWS, Google cloud platform, Microsoft Azure, many more websites who provide servers. I recommend you to use AWS or Google cloud platforms. They provide free trials. You need to register on that website and now you are Rady to launch your server. For more info, Google it.

For Your Ubuntu 16.04 Server you will need that :

RAM 4GB OR Higher.
Storage :200GB?+

### (2) familiar with the GitHub and Linux commands :
You need some knowledge about Github and Linux command. If you do not know that then font worries I will teach you some basics in that article. But if you want to learn like a pro then just Google it.

### (3) Required Any android phone :
You can use any android phone for compiling a ROMs.

### (4) Device sources Needed :
Every custom ROMs or any stock ROM build from your device sources. We will not talk about in deep. Just you need to know about device sources. In that device sources, 3 trees are required.

### Device sources :
Device tree.

kernel tree.

vendor tree.

Common tree (not for every device)

The above trees are required to build custom ROMs. Every device has its specific device sources.

### (5) Rom Source :
There are lots of custom ROMs available on the internet. Like lineage os, aosp extended, pixel experience, dot os, aokp, superior os, Syberia project etc. Select any rom and get the source from GitHub.

### (6) Download :
[sociallocker] JuiceSSH – SSH Client App. This app will help you to connect your server via SSH on Android.[/sociallocker]

## Now it's time for how to  Compile Rom 
So all steps are similar for every device. so without wasting time let’s get started.

### (1) create Ubuntu 16.04 server On AWS (Amazon Web Service) :
Just create an account on Amazon Web Services (AWS). After activation, you are ready to launch an instance. First, go to your AWS dashboard. Go to services / EC2 / Launch instance / Select Ubuntu 16.04 LTS. After that click on 8cpu 32GB RAM instance. Click on Next: Configure Instance Details. Now don’t need to set anything. Just click on Next: Add Storage. Here you will see SIZE (GB). 8 GB is by default. So you need to change it with 200GB. Now just click on Next: Add tags. Add any tag if you want. After that click on Next: Configure Security Group. You will get SSH group so just change source tab custom to Anywhere. Now click on Review and launch. Now you need to click on the Launch button. It will ask you for a key pair. If you doing all these things so just create a new key pair. Don’t forget to download that key pair on your pc or phone. My key pair name is Roshan.pem. After launching an instance you will get your public Ip on dashboard /services /EC2 / instance. copy your public IP address.

### (2) Connect Ubuntu 16.04 server via SSH on Android :
You need to install JuiceSSH – SSH Client app from the above link or from Google play store


#### You require 3 things to connect.

 #### Public IP Address.

 #### Keypair.
 
 #### USERNAME: ubuntu
 Open JuiceSSH – SSH Client App on Android. Go to Connections. Click on ➕ the plus icon to create a new Connection. Set it that like bellow :
 
#### Nickname: Any
#### Yupe: SSH
#### Address: put your public Ip

#### Identity: Add New.

In identity fill like bellow:

#### Nickname: any
#### Username: ubuntu
#### Private Key: select your key pair.
Save it. Done now your instance is connected on your Android phone. Now open your Ubuntu 16.04 server from connection tab. It will open a terminal. Done your instance is ready to use.

### (3) Setting Up Build Environment For Compiling ROM’s :
You need to install some packages for building a custom ROMs. So you need to copy-paste that commands one by one and press enter. # lines are an explanation of commands so don’t copy # lines

#### #get superuser access.

sudo su

#### #install JDK (press enter 2 times).

add-apt-repository ppa:openjdk-r/ppa

#### #update all packages.

apt-get update

#### #install more packages.

apt-get install bison build-essential curl ccache flex lib32ncurses5-dev lib32z1-dev libesd0-dev libncurses5-dev libsdl1.2-dev libxml2 libxml2-utils lzop pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev git-core make phablet-tools gperf openjdk-8-jdk -y

##### #become a normal user.

exit

#### #creating a bin folder.

mkdir ~/bin

PATH=~/bin:$PATH

cd ~/bin

curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > ~/bin/repo

chmod a+x ~/bin/repo

git clone https://github.com/akhilnarang/scripts.git scripts

cd scripts

bash setup/android_build_env.sh

Done now your instance is ready for Compile Rom From Source. We are going to compile any rome do you wants.
### (4) Create a Github account :
Guys if you want to Compile Rom From Source Without PC then you will need to get more information about Github. You can get the information from Google. But you need to have an account on GitHub. So go to github.com and create your new account. If you have an account already then use the old one. We required your Github: username and email address for a letter use.

### (5) Clone or Download ROM source :
Now finally we are going to download a lineage os 16.0 ROM source in our server. You can use your favourite Rom source if you want. For downloading source first follow these steps and copy-paste bellow commands In your server:

### create a Rom folder.

mkdir room name

(like I am creating a Havoc folder, so my command is mkdir lineage)

#### #Go to ROM folder.

cd lineage

(replace lineage with your folder name).

#### #Connect your Github account.

git config –global user.email “EMAIL” && git config –global user.name “USERNAME”

(Remove EMAIL and put your email. Remove USERNAME and put your username.) like this :

git config –global user.email “anandanubhav1516@gmail.com” && git config –global user.name “anandanubhav1516”

You need to understand some Github Commands.

git clone – git clone Command use for downloading repositories from GitHub.

branch (-b) – brach is defined for which brach you want to use. Like pie brach, oreo brach, Android Q brach etc.

#### #To initialize lineage os 16.0 source.

repo init -u git://github.com/Havoc/android.git -b Havoc-16.0

#### #To sync up or downloading source.

repo sync

After repo sync, it will take a lot of time to download your source. Because sources are large in size like 30-40 GB. So wait until its stop downloading

### (6) What is Device sources:
After downloading the Rom source. Now you need to know your device code name from Google. If you don’t know how to check the code name of your device. Just google it like code name of your device name. Like the code name of xiaomi MI Max 2. So in my case, my xiaomi MI Max 2 device code name is oxygen. The code name is needed guys. Now we need to clone Device sources. Like kernel tree, device tree, vendor tree. You can find your device sources from xda or GitHub. So find your tall trees first. If your phone has any custom rom available then go to that xda post. There you will get your device sources in the sources tab.
You can also search your device sources in the Github search bar. Like I want device tree for my xiaomi Mi Max 2 oxygen. So I am going to search like that :

For the device tree :
device_xiaomi_oxygen

For kernel tree :

#### Kernel_xiaomi_oxygen

OR

#### Kernel_xiaomi_msm8953

(msm8953 is my device chipset. So you may be different. So google it your device chipset).

####For Vendor Tree :

#### Vendor_xiaomi

OR

#### Vendor_xiaomi_oxygen (sometimes).

#### For Common Tree :

device_xiaomi_msm8953-common

If this tree available for your device. Then you must use this tree as well. So the question is how we know a common tree is available for my device or not?. So simple is that go to your device tree / rom.dependencies file. Open that file. If you will see a common tree in that file. So you need to clone that tree also. If not then live it.

I hope you will find your device sources for your device. Now we are going to clone our device sources like that. Format to clone trees:

#### git clone URL -b BRANCH PATH

#### URL: put your source URL.

#### BRANCH: select your branch name from trees.

#### PATH: whare you clone your sources in your server


 

