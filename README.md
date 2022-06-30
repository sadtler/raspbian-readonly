# raspbian-readonly

Credit goes to the following people
- [niun](https://gist.github.com/niun/34c945d70753fc9e2cc7)
- [chesty](https://github.com/chesty/overlayroot)
- [JasperE84](https://github.com/JasperE84/root-ro)
- [josepsanzcamp](https://github.com/josepsanzcamp/root-ro)

They did the actual work, I simply modularized the scripts for my own convenience, configured them so the pi user can run them (no need to sudo su) and created a single command installation.

Run the command below on a clean, minimal installation of Raspbian Stretch.

```
bash <(wget --no-check-certificate -qO- https://raw.githubusercontent.com/sadtler/raspbian-readonly/master/install)
```

Everything will be set up, and after reboot the system will be read-only.

**Reboot to read/write mode (disable overlay fs)**
```
/home/pi/rw-mode
```
**Reboot to read-only mode (enable overlay fs)**
```
/home/pi/ro-mode
```
**Enter temporary write access mode**
```
sudo mount -o remount,rw /mnt/root-ro
chroot /mnt/root-ro
```
**Exit temporary write access mode**
```
exit
sudo mount -o remount,ro /mnt/root-ro
```
