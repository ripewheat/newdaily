# Connecting to an Android device over SSH

## Initial Setup

Install Android App Termux from APKPure or AppStore. If the app exists, just delete and re-install it to get the latest version, The APK can be downloaded from https://apkpure.com/termux/com.termux/ Install the APK using by running

```
adb install ~/Downloads/Termux_v0.73_apkpure.com.apk
```

Then locate the app and run it

## Install and run SSH Server

Next, run the following commands inside the Termux using the on device keyboard to type. When the setup asks for permission, always choose default option, you can just hit/tap enter on the keyboard, dont let it modify any configs

```
pkg install root-repo
pkg upgrade
pkg install openssh
```

Now, set a password for the current user by running `passwd`, remember this password you will need it later

Then, Start the SSH server inside by running `sshd`, do not close/exit the app after running the command

## Connect to SSH Server

On the pc terminal run the following, dont use `root@` as prefix to the ip address

```
ssh <ip address of android device> -p 8022
```

When asked for password, enter the password you used in the steps above

This will drop you into a shell where you can do further installs using `pkg install <name>` or run any other command you would like `wget, curl` you get a proper linux shell, sweet, enjoy!

## Stop SSH Server

Once you are done working with the shell, stop the ssh server by running `pkill sshd` on the device

## Troubleshooting

### Host key verification error

If for some odd reason you are getting Host key verification failed error, run the following first

```
ssh-keygen -R <ip address of android device>
```

If it still gives you trouble edit `~/.ssh/known_hosts`, locate the line(s) with the ip address and delete it and then connect again

### Waiting forever to connect

There are instances when the pc to android ip connection will wait a long time. If so, first check if you can ping the android's ip address, and if its not pingable, perhaps reboot the android device. Stating the obvious here, unless the android cant be pinged you cant ssh into it.

## Reference

Extracted from Termux's wiki on this topic from here [https://wiki.termux.com/wiki/Remote_Access] it describes alternate ways using Dropbear, Mosh and RSync