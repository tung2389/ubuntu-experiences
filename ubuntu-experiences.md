Ubuntu experiences (when I messed up my computer with three desktop environments: Ubuntu, Xubuntu and Lubuntu) :

- Change lock screen: /etc/lightdm/lightdm.conf (lightdm is the display manager of ubuntu. You may need to change some other files because it bases on them)

- Change splash screen : /usr/share/plymouth/themes/default.plymouth. Plymouth controls your screen when you star-t or turn off your computer.

- "grep" and "find" are very useful commands to delete all remnants of old desktop environments,

- Change the file /etc/acpi/powerbtn.sh or /etc/systemd/logind.conf if you want to change the option when push shutdown button. Ex: put a command like "shutdown -h now" in the beginning of the file.

- Change default sessions : /var/lib/AccountsService/users/username

- Change libre office and fonts:
Tools > Options > LibreOffice Writer > Basic Fonts (Western)
/usr/local/share/fonts

- Change display brightness :
/sys/class/backlight/intel_backlight/brightness

- See all desktop environments:
ls /usr/share/xsessions/

- Disable a device in your computer :
xinput list: list all your device and their id.
xinput set-prop DEVICEID "Device Enabled" 0: to turn off
xinput set-prop DEVICEID "Device Enabled" 1: to turn on
- Disable touchpad when typing:
/home/your_usr_name/.config/your_session/your_desktop_environment/autostart
syndaemon -d -t

- Install some Microsoft regular fonts:
sudo apt install ttf-mscorefonts-installer
sudo fc-cache -f -v

- Restart lightdm:
sudo service lightdm restart

- Shorcut for deepin control center:
dbus-send --print-reply --dest=com.deepin.dde.ControlCenter /com/deepin/dde/ControlCenter com.deepin.dde.ControlCenter.Toggle

- Fix some bugs about shorcut of deepin in /usr/share/applications ( must mutate by root user with nano or something like that).

- Update default version of gcc:
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-8 

- gdbus error org authentication required (when suspend):
https://www.reddit.com/r/xubuntu/comments/8w23gu/how_to_fix_the_suspend_on_inactivity/

- If everytime when you try to suspend your computer, it requires password (authentication required), then you can turn it off by:

+ Open the file /usr/share/polkit-1/actions/org.freedesktop.login1.policy with root user.
+ find the line: <action id="org.freedesktop.login1.suspend">
+ Below this line, check if its content is same to these ( if not, change it) 
```
<defaults>
    <allow_any>yes</allow_any>
    <allow_inactive>yes</allow_inactive>
    <allow_active>yes</allow_active>
</defaults>
```
