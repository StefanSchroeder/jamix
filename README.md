# jamix
Proof-of-concept video telephony linux setup for non-technical users 

The idea behind Jamix is that we want to create a Linux setup (and perhaps an entire distro) that
does only one thing well. Allow non-tech-savvy users to place and receive video calls.

It shall run on obsolete laptops or PCs or raspberr Pi's.

It's almost impossible to pre-configure a system absolutely without zero-configuration, 
but we are striving for it.

When booted, the system can only one of two things: Place a call to a preconfigured partner,
receive calls from preconfigured partners.

The system shall be useable with a single button (Make call or Hang up).

A call that is received is automatically taken.

# Prereqs

You need:

- A computer that can run Linux (a laptop, a PC or a raspberry pi).
- A camera (let's assume it's a USB-camera)
- A microphone (let's assume it's a USB-microphone)
- For ease of use: A USB gamepad with colored buttons.
- internet access (LAN or Wifi)

# Concept

We will install a Linux distro (Ubuntu on PCs, Raspbian on RPi).
We autologin to an Openbox Windowmanager session.
We run the following tools:
1. Jami, for video telephony
2. antimicro, to read the gamepads buttons
3. xloadkeys, to make the buttons do what we want
4. devilspie2, to control the window settings of Jami
5. feh, to show slideshows when no calls are taking place.

# Workflow

1. Booting
2. Starting X11
3. Starting Openbox
4. Starting Jami fullscreen
5. Idle
6. if call received automatically pick up. On button, hangup. Goto 5.
7. If button, place call. On button, hangup. Goto 5.
8. On long idle, start slides.

Stretch-goals:

- Use voice-recognition for control. (jasper?)
- Use open-cv pattern regognition for control (opencv!)

# Configuration

1. Tech-support needs to configure the Wifi, if any.
2. Tech-support needs to setup the initial Jami-user.


# Bootstrap

  sudo apt install openbox devilspie2 antimicro xloadkeys

Files we need to take care of:

~/.dmrc (select session, WM)

~/gameppad_remaps.gamecontroller.amgp

~/.xbindkeysrc

~/.config/antimicro/antimicro_settings.ini

~/scripts/*
