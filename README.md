# Personal Fedora 32 Notes

* [Java](#java)

## Remove

	sudo dnf remove konqueror calligra-libs falkon krfb dnfdragora
    
## Install

	sudo dnf install gnome-icon-theme breeze-gtk gsl dnfdaemon dnfdaemon-selinux libyui libyui-qt libyui-mga-qt \
	libyui-ncurses libyui-qt-graph python3-dnfdaemon python3-pyyaml python3-yui

## Java


### Open JDK 8

	sudo dnf install java-1.8.0-openjdk java-1.8.0-openjdk-devel java-1.8.0-openjdk-headless \
	java-1.8.0-openjdk-javadoc java-1.8.0-openjdk-demo java-1.8.0-openjdk-openjfx openjfx
	
	

#### Virtualization (Only one)

	sudo dnf group install --with-optional virtualization


### TLP

	sudo dnf install tlp tlp-rdw

[Linrunner.de](http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html#installation)

### Speed up LibreOffice

	sudo dnf group install LibreOffice


### Chromium

	You will need RPMFusion's repo
	sudo dnf install chromium-freeworld

## Graphics

### Gimp

	sudo dnf install gimp gmic-gimp gimp-help gimp-resynthesizer

### Design

	Download from https://www.appimagehub.com/p/1288974
	chmod +x Inkscape-9dee831-x86_64.AppImage
	./Inkscape-9dee831-x86_64.AppImage

## Development

	dnf groupinstall "Development Tools" "Development Libraries"

## Disable MCE Check

	vim /etc/abrt/plugins/oops.conf
	OnlyFatalMCE = yes


## Multimedia

### Players

	sudo dnf install vlc juk
    
### Media Codecs

	sudo dnf install amrnb amrwb faac faad2 flac gstreamer1-libav gstreamer1-plugins-bad-freeworld \
	gstreamer1-plugins-ugly gstreamer-ffmpeg gstreamer-plugins-bad-nonfree gstreamer-plugins-espeak \
	gstreamer-plugins-ugly lame libdca libmad libmatroska x264 xvidcore gstreamer1-plugins-bad-free \
	gstreamer1-plugins-base gstreamer1-plugins-good gstreamer-plugins-bad

### VA-API

	sudo dnf install libva libva-utils libva-intel-driver libva-intel-hybrid-driver

#### Check Status

	vainfo

### VDPAU

	sudo dnf install vdpauinfo libva-vdpau-driver libvdpau-va-gl

#### Config

    # VDAPU Support
    export VDPAU_DRIVER=va_gl

#### Check Status

	vdpauinfo
	
    
#### Plasma with gstreamer

	sudo dnf install gstreamer{1,}-{ffmpeg,libav,plugins-{good,ugly,bad{,-free,-nonfree}}} --setopt=strict=0

#### Plasma with Phonon

	sudo dnf install phonon-qt5-backend-gstreamer phonon-backend-gstreamer


## Apps

    sudo dnf install keepassxc vim

## Utilities

    sudo dnf install youtube-dl htop powertop python3-dnf-plugin-tracer pandoc nmap ImageMagick \
    lm_sensors unrar simple-mtpfs

## KDE Apps

    sudo dnf install digikam soundkonverter
	
## KDE Utilities

    sudo dnf install k3b-extras-freeworld akonadiconsole kdesdk-thumbnailers ffmpegthumbs unar kio_mtp

## Fonts

    sudo dnf install levien-inconsolata-fonts adobe-source-code-pro-fonts \
    adobe-source-sans-pro-fonts open-sans-fonts google-noto-emoji-fonts \
    google-noto-sans-old-turkic-fonts mozilla-fira-mono-fonts

### Microsoft Core Fonts

    sudo dnf install cabextract
    sudo rpm -i https://downloads.sourceforge.net/project/mscorefonts2/rpms/msttcore-fonts-installer-2.6-1.noarch.rpm
    
[mscorefonts2 Sourceforge](http://sourceforge.net/projects/mscorefonts2/?source=typ_redirect)


### Suspend to Disk

    sudo nano /etc/default/grub
    sudo blkid
    GRUB_CMDLINE_LINUX="resume=UUID="swap-partition-uuid"
    sudo grub2-mkconfig -o /boot/efi/EFI/fedora/grub.cfg


### Screencasting
    
    sudo dnf install key-mon simplescreenrecorder ffmpeg
    
## Video Editing

    sudo dnf install kdenlive frei0r-plugins obs-studio
	

## Write disk using ddrescue

    sudo dnf install ddrescue
    Example: sudo ddrescue -D --force kubuntu-19.10-desktop-amd64.iso /dev/sdb


## SDKMAN

	export SDKMAN_DIR="/home/sudhir/.local/bin/sdkman" && curl -s "https://get.sdkman.io" | bash sdk install gradle


## Lock a package version

	sudo dnf install python3-dnf-plugin-versionlock
	dnf versionlock add package-name

## Write ISO to the usb

	sudo dd bs=4M if=F31-KDE-x86_64-LIVE-20200408.iso  of=/dev/sda status=progress oflag=direct
