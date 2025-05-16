# Rokoko Studio setup for Linux

It is possible to make the Rokoko stack work on Linux. However, at the moment this includes several steps, and the USB connections are not working for the time being!

- The Ubuntu version used in this guide is Ubuntu 24.04.2 LTS (Noble Numbat)

## Rokoko studio

This guide uses Lutris as the tool to manage the location and running configuration of Rokoko studio.

![Screenshot From 2025-02-13 10-39-05](https://github.com/user-attachments/assets/c4a89333-32d5-4127-be7e-bb460ca26d00)

Support for Windows video games running on Linux is really good and this means that a lot of Windows applications can run as well! So don't fret when Lutris references video games, it's just all the work in recent years for Linux to run windows applications is focused on video games!

### Installing Lutris (pre-requisite)

Lutris can be installed using the standard commands from any major Linux distribution. 

#### Ubuntu

Download the deb package from [the lutris repo](https://github.com/lutris/lutris/releases) and install it using apt

```sh
sudo apt install ./lutris_0.5.18_all.deb
```

#### Fedora

```sh
sudo dnf install lutris
```

#### Others

An extensive list of how to install Lutris can be found [here](https://lutris.net/downloads)


# Setting up Lutris

- Go to Lutris preferences:

![Screenshot From 2025-02-13 10-42-34](https://github.com/user-attachments/assets/15042122-fe34-44f2-8350-dfe30da25555)

- Click Updates
- Download wine-ge-8-26

Bare in mind that this is an older version (but it currently works quite well). 

Other options as runners can be found under the Runners section. Find wine, click the box icon and select any version you want to try!

![Screenshot From 2025-02-13 10-45-43](https://github.com/user-attachments/assets/2fb3ca40-ba1e-40bb-bec9-23a36293f3a4)

In the example below, wine-ge-8-26 and lutris-7.2.2 are installed. Both are different versions of wine. See the ( [Wine Flavours for advanced users](#wine-flavours-for-advanced-users)) section
for a list of other community supported flavours!

![image](https://github.com/user-attachments/assets/48979ebe-9e9d-4668-aec6-e82730e1257f)

### Running Rokoko Studio on Linux

#### Download official Rokoko studio installer

The first step is to download the official installer from Rokoko!

![Screenshot From 2025-02-13 10-39-57](https://github.com/user-attachments/assets/9b060089-cb56-4ef0-a6d7-e668ffbc8530)

At the point of writing, the downloaded version is `2.4.5.0` .

#### Installing Rokoko studio on Linux with Lutris

Adding a video game or windows application is fairly straightforward, but in the case of Rokoko studio, one must just be aware that the installation appears to be stuck (although it is completed without issues)

Having that in mind, the process is better controlled by choosing the `Add locally installed game` option! 

![Screenshot From 2025-02-13 10-40-43](https://github.com/user-attachments/assets/03b7ae90-f8b7-4640-9a2e-933d99f06750)

- Next step, under **Game Info**, complete the Name that you want to appear (e.g. Rokoko Studio) and for Runner choose `Wine (Runs Windows Games)`

![Screenshot From 2025-02-13 10-41-00](https://github.com/user-attachments/assets/75f75d53-ee0a-4ed7-9248-77a8faddb767)

Under **Game options**:
- choose the executable of the Rokoko studio that you downloaded
- For wine prefix, click the `...` icon, create a new folder in your home directory called rokoko_wine (the name doesn't matter) and click save

![Screenshot From 2025-02-13 10-41-41](https://github.com/user-attachments/assets/8506acc8-e5dc-44a8-bc27-733238f09b69)


Under **Runner options** select the wine version you want! If you don't see a System wine version, you can install wine on your system (follow the [Install Wine Guide](#Install Wine Guide) or [Setting up Lutris](#setting-up-lutris)

![Screenshot From 2025-02-13 10-41-56](https://github.com/user-attachments/assets/02b3803b-7add-45a4-85b9-506b8381f81a)


Click save.

#### Run the installation

Select Rokoko Studio from the Lutris main view and click Play

![image](https://github.com/user-attachments/assets/7714b6ce-e7e4-4ffe-b4b7-2a702dd620df)

This will bring the Rokoko installer up!

![Screenshot From 2025-02-13 10-27-21](https://github.com/user-attachments/assets/89bf0191-68ee-4e07-bf69-1856282e0569)

Depending on the wine flavour you selected, you may see the message below pop up!

![Screenshot From 2025-02-13 11-00-04](https://github.com/user-attachments/assets/ccee0b4b-e31e-4e0e-a769-f19901924613)

Click install! Mono runtime is important as is the .NET equivalent for Linux!

The process will finish but it will most probably be stack, so the windows will disappear but Lutris won't recognise that the application has stopped! Wait a few seconds for good measure and then stop the application manually!

#### Run Rokoko Studio

Since we configured our "Lutris Game" to run the installer, we now need to switch it to the Rokoko application.

Click on the Rokoko Studio "Lutris Game" again, but instead of play, click the arrow up button next to it!

![image](https://github.com/user-attachments/assets/c22be552-fd77-4fcd-b9e6-33528c477f9d)

Then click Configure!

Go to game options and next to executable click the `...` icons!

Navigate to the Rokoko prefix directory configured in [Installing Rokoko studio on Linux with Lutris](#installing-rokoko-studio-on-linux-with-lutris) and find 
the Rokoko executable in `drive_c > Program Files (x86) > Rokoko Electronics ApS > Rokoko Studio > Rokoko Studio.exe`

- Click save again!

- *****************************Change the different versions in the Runner options panel because Rokoko Studio will not open********************

Before clicking Play, note that the Rokoko installer will come up again! This is because Rokoko Studio will realise there is a newer version. The installation process will be
repeated and at the end you'll need to click Stop manually again. On clicking play again, you'll be prompted to login:

At the time of writing the most recent version is `2.4.8.0` and you'll see it (or a more recent one) at the bottom right of the opening window

![Screenshot From 2025-02-13 10-57-23](https://github.com/user-attachments/assets/1fdfb0f3-3a63-458b-887b-0777f7ccd30e)


#### Proton-GE

A well known community Proton fork, is Proton-GE, which uses the latest versions of wine, dxvk and vulkan-d3d, while the mainstream Proton uses more stable versions! Proton-GE, while cutting edge, allows more games to be played in the price of stability. In practice, this is what we need to setup.
Setting up the environment

First, we need to install the umu-launcher. You can find the latest release here.

This guide, will use the latest release at the point of writing, 1.2.5.
Install UMU

This step, slightly differs for each distribution, Ubuntu 24.04 (Noble Wombat) and Fedora 41 examples are provided as reference! After UMU is installed, the rest of the steps are the same!
Ubuntu 24.04

Download python3-umu-launcher_1.2.5-1_amd64_ubuntu-noble.deb and umu-launcher_1.2.5-1_all_ubuntu-noble.deb .

Install them both

sudo apt install ~/Downloads/python3-umu-launcher_1.2.5-1_amd64_ubuntu-noble.deb

sudo apt install ~/Downloads/umu-launcher_1.2.5-1_all_ubuntu-noble.deb

Fedora 41

sudo dnf install ~/Downloads/umu-launcher-1.2.5.fc41.rpm

Verify installation

Check umu-run is now available system wide

which umu-run 

/usr/bin/umu-run

Install Proton-GE

Head to the Proton GE releases and you download the most recent version. At the moment of writing the most recent version is 9-25 . You can also choose to use this instead of the latest, unless a long time has passed since the writing of this document.

wget https://github.com/GloriousEggroll/proton-ge-custom/releases/download/GE-Proton9-25/GE-Proton9-25.tar.gz 

After downloading we need to extract the contents. You can do so like this:

Create the directory to extract the contents to (this can be the compatibilitytools.d in steam, so if you have steam, this proton version will also be available for any steam games you play or applications you run)

[ -d ~/.steam/root/compatibilitytools.d/ ] || mkdir -p ~/.steam/root/compatibilitytools.d/

Copy the file and extract:

mv ~/Downloads/GE-Proton9-25.tar.gz ~/.steam/root/compatibilitytools.d/
cd ~/.steam/root/compatibilitytools.d/
tar -xvf ~/Downloads/GE-Proton9-25.tar.gz

Now we are ready to go back to Lutris. If you have chosen a different directory than ~/.steam/root/compatibilitytools.d/ , it's ok, just remember to use it in the follow-up instructions!
Setup Lutris to use Proton for Rokoko Studio

In the runner options, with Advanced enabled select Custom for wine version!

Select Wine Custom

In the custom wine executable put the location of umu-run as shown in Verify Installation

Insert UMU run executable

Then go to system options and scroll down until you see Environment variables under Game execution!

Find Environment variables

We need to tell UMU now, where to find our preferred version of Proton! We do so with the PROTONPATH environment variable, as described in UMU documentation

In the environment variables click Add and in the Key column put PROTONPATH and in Value column the location where Proton-GE was extracted from Install Proton-GE

PROTONPATH configuration

Click save!
Run the application

First, we need to make sure that our changes have taken effect. We can display the logs while running the application, by selecting Show Logs

Show Logs

Then click Play!

The logs should show at the top something like

lutris-wrapper: Rokoko Studio
Started initial process 175620 from gamemoderun /usr/bin/umu-run /home/rokoko/Downloads/.pfx_rokoko/drive_c/Program Files (x86)/Rokoko Electronics ApS/Rokoko Studio/Rokoko Studio.exe

The application should start up!

At the point of writing, the UMU method with the versions described is the most reliable way to run Rokoko Studio and both Browser authentication and the UI should work.

This advanced setup fixes the following issues described in Rokoko Studio:

    Installation hangs (never exits), so both the basic installation and the update happen in a single run
    Authentication with a browser when using the Lutris proton-ge version
    UI not usable when using system wine (either version 9 or 10)





















========================================================================================================================
#### Try out

- Make sure your graphics behave properly by opening a Rokoko provided animation and playing the scenes!

https://github.com/user-attachments/assets/8a18281b-5d8d-448a-9316-0a441c4cc4f4

- USB pairing is not working at the moment, so if you want to pair a suit, you'll have to connect it to a Mac or Windows device in the same network. Pair it with the WiFi
but use the local IP address of the Linux machine.

You can find the local IP using 
```sh
ifconfig 
```

![image](https://github.com/user-attachments/assets/2fd4af5a-3cc3-4609-8038-37379a6c1a6d)

Or 
```sh
ip address show
```

![image](https://github.com/user-attachments/assets/bdb6edbd-ff52-4481-888f-08bda8e4652f)

In the above cases, the local ip is `192.168.0.25`

In the example below, a mac was used to pair a glove, with the Linux laptop, with these steps:

1. Connect the glove to the macbook via usb and wait for it to be recognised
2. Click on the device (top right) and open wifi settings
3. Provide the Wifi details and click advanced settings. Use the IP from the previous step

![image](https://github.com/user-attachments/assets/929d9e98-9e03-4dd2-b98b-f23aba6a44bc)

##### Unreal Engine integration with Rokoko Studio

Now, you can open Rokoko Studio again on Lutris!

Connect your Glove (or suit!) to some power source and make sure it's connected to the wifi! It should then show up on the Rokoko Studio running on Linux!

![Screenshot From 2025-02-14 17-16-36](https://github.com/user-attachments/assets/ea8b30ed-081a-4473-8958-ab43ec0c87a6)


![image](https://github.com/user-attachments/assets/7c9a5ec3-a5b2-44e8-8288-239abbb038b3)


#### Troubleshooting

##### Sign in with Browser not working

This is a known issue with `wine-ge-8-26` . You can temporarily switch to the system wine version to get past the sign in screen, close Rokoko, switch back to
`wine-ge-8-26` and then run Rokoko again! For a universal solution, you can follow [Advanced Setup](/Advanced%20Setup.md)

##### UI is not working/buttons are not clickable

This is a known issue with the system versions of wine (either 9 or 10). Switch to `wine-ge-8-26` described in [Setting up Lutris](#setting-up-lutris) or
setup Proton to run Rokoko Studio following the instructions in [Advanced Setup](/Advanced%20Setup.md)

##### Crashes and graphical issues

Some crashes might be related to your Graphics hardware. You may find the [Graphics Setup Guide](/Graphics%20Guidelines.md) useful in deciphering the state of 
graphics in Linux against your situation!

