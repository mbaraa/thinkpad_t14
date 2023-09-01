# thinkpad_t14
Lenovo ThinkPad T14 Gen3 configuration files for Linux. 


Lenovo is hating on Linux lately, that is some stuff are not working out of the box!

### Audio Issues:
- For startes make sure that your user is added to the `audio` group
  `sudo gpasswd -a $USER audio`
- Intel's `dmic_detct` is making Linux not able to see the audio card, so you're gonna need to disable it :)
- Add this to `GRUB_CMDLINE_LINUX_DEFAULT` inside the file `/etc/default/grub`
  ```
  snd_hda_intel.dmic_detect=0
  ```
- Run `sudo grub-mkconfig -o /boot/grub/grub.cfg`
- Reboot :)

### NVMe Issues:
- Well, this is a problem that has been in Linux since NVMes were invented, and fixing it is quiet easy
- Add this to `GRUB_CMDLINE_LINUX` inside the file `/etc/default/grub`
  ```
  nvme_core.default_ps_max_latency_us=0
  ```
- Run `sudo grub-mkconfig -o /boot/grub/grub.cfg`
- Reboot :)
