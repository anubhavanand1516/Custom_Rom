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


### (7) Clone your device sources :
Now I am going to clone my sources now. So if you are building the same device like xiaomi Mi Max 2 then you can use these commands without changing anything. If you are using another device then use your device source URL, BRANCH, and PATH.

#### #make sure you are in the Rom folder (in my case it is lineage). If you are not in the Rom folder then go using the cd command.

cd lineage

#### #device tree.

git clone https://github.com/MaheshTechnicals/android_device_xiaomi_oxygen.git -b pixel device/xiaomi/oxygen

#### Sometimes it’s according to your tree.

git clone https://github.com/MaheshTechnicals/android_device_xiaomi_oxygen.git -b pixel device/xiaomi

#### #Kernel Tree.

git clone https://github.com/MaheshTechnicals/Kernel_xiaomi_oxygen -b lineage-16 kernel/xiaomi/msm8953

#### #Vendor Tree.

git clone https://github.com/MaheshTechnicals/android_vendor_oxygen -b lineage vendor/xiaomi

##### Sometimes it’s according to your tree.

git clone https://github.com/MaheshTechnicals/android_vendor_oxygen -b lineage vendor/xiaomi/oxygen

#### #Common Tree.

git clone https://github.com/rakeshraimca/android_device_msm8953-common -b havoc-new device/xiaomi/msm8953-common

#### Done. Now you’re all device sources are cloned. Now we are moving for the next step.

### (8) Rom Bring up Or Fixing Device Tree :
Guy’s Rom + Device sources are cloned successfully. But now we are going to do Rom bringup. In simple words, you are going to connect your device sources with ROM Source. For that, you need to modify some files in your Device Tree. So first go to your device tree using a command from Rom folder.

#### #going to device tree folder.

cd device/xiaomi/oxygen
 

#### #what file and folders we have.

ls

You will see lots of files and folders. But we need to modify only five files. So which files we need to modify? listed here :

rom.dependencies
rom_oxygen.mk
vendorsetup.sh
AndroidProducts.mk

#### #Let’s start with a first file. You need to rename rom.dependencies file to your room name.dependencies. we will use mv command for rename files and folders. In my case, I am building lineage os so the command is.

mv rom.dependencies lineage.dependencies

#### #rom_oxygen.mk rename according to your ROM.

mv rom_oxygen.mk lineage_oxygen.mk

according to the Rom, it will change like in pixel experience Rom it will be rename like aosp_oxygen.mk

You can refer this from official device sources of another device. Like if you want to know lineage os device tree modification, then search in Google like lineage device git. And refer to any device tree.

#### #create or modify vendorsetup.sh file.

nano vendorsetup.sh

#### #it will open that file. Clear all lines if you have and add some lines from bellow :

add_lunch_combo rom_codename-userdebug

Replace Rom with lineage (according to your Rom name). Replace code name with your device code name. Like in my case my command is

add_lunch_combo lineage_oxygen-userdebug

#### #Save vendorsetup.sh file. You need to press :

#### CNTRL+O
#### ENTER
#### CNTRL+X

#### #AndroidProducts.mk. We need to open this file.

nano AndroidProducts.mk

#### #replace with your Rom name and device code name like this :

PRODUCT_MAKEFILES := \
          $(LOCAL_DIR)/lineage_oxygen.mk

#### #Save AndroidProducts.mk file.

#### CNTRL+O
#### ENTER
#### CNTRL+X

#### #Now we need to change some lines in lineage.mk file. open lineage.mk file.

mano lineage_oxygen.mk

#### #replace with Rom config file and Rom name like this :

$(call inherit-product, vendor/lineage/config/common_full_phone.mk)

#### #change Rom name in that line.

PRODUCT_NAME := lineage_oxygen

#### #Save lineage.mk file.

#### CNTRL+O
#### ENTER
#### CNTRL+X

Done your device tree is now fixed. So now your device tree is properly connected to your Rom source. Now you are ready to build your first Rom.

### (9) Build Or Compile Your ROM :
After all these steps you are ready to Compile Rom From Source Without PC. So, guys, let’s start building or start a compilation of your Rom. Just follow the commands.

#### #first go to Rom folder for that.

cd

cd lineage

#### #Run build script.

. build/envsetup.sh

#### #Run caches.

export USE_CCACHE=1 && ccache -M 50G && export CONFIG_STATE_NOTIFIER=y && export SELINUX_IGNORE_NEVERALLOWS=true

#### #lunch your device. With your device code name like this.

lunch lineage_oxygen-userdebug

#### #Brunch your device. And put your device code name mine is oxygen so.

brunch oxygen

OR

make bacon

It will start Compiling a Rom For Your device. It will take 2-3 hours (it totally depends on your servers CPU and RAM) to build Rom so wait until 100%.

### (10) Getting errors! How to fix those errors :
If your Rom building stop by getting some errors? So you need to fix that errors first then compile again. If you are getting some error. Then cuppy that some error lines and search it on Google to fix. Then it will fix. Because mostly all errors and solutions you will get from Google. After fixing and error you need to follow to start building again.

If you really search on Google but not getting any solutions. Then i will give you some telegram groups. Ask your questions there. They will definitely help you.

#### #first go to Rom folder for that.

cd

cd lineage

#### #Run build script.

. build/envsetup.sh

#### #Run caches.

export USE_CCACHE=1 && ccache -M 50G && export CONFIG_STATE_NOTIFIER=y && export SELINUX_IGNORE_NEVERALLOWS=true

#### #lunch your device. With your device code name like this.

lunch lineage_oxygen-userdebug

#### #Brunch your device. And put your device code name mine is oxygen so.

brunch oxygen

OR

make bacon

### 11. Upload ROM On Your Google Drive:
After compile successfully. You need to transfer your ROM zip file to your Google Drive Account. For that, you will need a Gmail account. I don’t think so if anyone does not have that in this world. But if you did not have it then create that from Google drive website.

OK so now we are ready to upload our first lineage os Rom on your google drive account. So follow the commands.

#### #go to the home directory.

cd

#### #setup Google Drive.

wget https://docs.google.com/uc?id=0B3X9GlR6EmbnWksyTEtCM0VfaFE&export=download

#### #Rename to gdrive.

mv uc\?id\=0B3X9GlR6EmbnWksyTEtCM0VfaFE gdrive

#### #set permissions.

chmod +x gdrive

#### #install drive package.

sudo install gdrive /usr/local/bin/gdrive

#### #get a link.

gdrive list

After that command, you will get an authentication link in your terminal. So copy that link and paste in any browser. I am going to paste that link in my chrome browser. They will ask you to connect your Google account there. So just click on your Google account. Then they give you a verification code copy that code and paste it in your terminal then press enter.

Done. Now your Google drive account is connected to your Ubuntu server. Now we are going to upload our Rom file.

#### #go to your Rom zip file. Replace with your code name.

cd lineage/out/target/product/oxygen

ls

#### #find your Rom file name. upload your ROM zip file to drive. Replace Rom.zip to your Rom file name.

gdrive upload Rom.zip

Done now your ROM zip file will upload on your Google Drive. So now go to your Google Drive account or Google drive app. Log in with same email ID which you used to connect the drive in a terminal. So download from it and test your Rom file.

### 12. Upload Your ROM’s On Android File Host (AFH) Server Via Terminal:
Guys if you are a developer then you should have knowledge about AFH. Android File Host provides cloud storage for your projects and other stuff. So if you want to upload and share your projects with others you can use that service for free. Finely we have our Custom Rom Rady to share with your friends. So now we are going to upload our ROM file into the AFH server via terminal. Let’s start.

#### (1) First, create an account on androidfilehost.com.

#### (2) Now request them via email for developer access. They will inform you via email.

#### (3) If you will get your developer account. Now we need FTP access. Just again contact them via email and request for FTP access. It will take 2-3 days.

####(4) After 2-3 days they will inform you. They will send your FTP Details like :

An FTP server: uploads.androidfilehost.com

FTP username: xxx

FTP password: xxx

FTP port: 21

SFTP port: 23

Save that details.

#### (5) first, go to that directory where your Rom file is present. Mostly is in out/target/product/oxygen. Now we are ready to upload files On AFH with a terminal via FTP. You need a command for it. See the command below :

curl –ftp-pasv -T FILENAME ftp://USERNAME:PASS@uploads.androidfilehost.com

NOTE: You need to replace some lines according to your details like example

FILE NAME: Name of your Rom file (AospExtended-v6.7-oxygen-20191206-1340-UNOFFICIAL.zip)

USERNAME: put your FTP username here.

PASS: Put your FTP Password.

#### (6) After modifying the above command according to your details. Just press enter. Your Rom will start uploading on AFH. It will take 1-2 minutes to complete.

#### (7) now go to your AFH Account. import your uploaded file from the FTP section. Done now your Rom file is on AFH. Share your ROM File with your device community or on xda.

## NOW USED YOUR CUSTOM ROM WITH NEW FEATURE AND LOT OF CUSTOMIZATION.



 

