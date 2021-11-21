Reboot 2 Windows
----------------

I am currently dual booting my home computer with Debian & Windows.
This is an easy script that uses `grub-reboot` to change the saved system to boot
from debian (default) into windows as a once off for gaming.
When ever I want to get back to debian, a simple reboot swings into linux :)


The setup
---------

You need to have grub setup to to use `saved` as the GRUB_DEFAULT.
You can do this by updating `/etc/default/grub`


    sudo sed 's/\(GRUB_DEFAULT\)=.*/\1=new_value/g -i /etc/default/grub

    sudo update-grub
	Generating grub configuration file ...
	Found background image: /usr/share/images/desktop-base/desktop-grub.png
	Found linux image: /boot/vmlinuz-4.7.0-1-amd64
	Found initrd image: /boot/initrd.img-4.7.0-1-amd64
	Found linux image: /boot/vmlinuz-3.16.0-4-amd64
	Found initrd image: /boot/initrd.img-3.16.0-4-amd64
	Found Windows Boot Manager on /dev/nvme0n1p2@/EFI/Microsoft/Boot/bootmgfw.efi
	Adding boot menu entry for EFI firmware configuration
	done


Clone down `reboot2windows` and setup a sym-link.

     git clone https://github.com/daniellawrence/reboot2windows
	 ln -s $PWD/reboot2windows/reboot2windows /usr/bin/

The symlink lets you easily update the script if needed, via a git pull

How to run
----------

As any user in the sudo group, you should just be able to invoke `reboot2windows`

    $ sudo reboot2windows
	Reboot into 'Windows Boot Manager (on /dev/nvme0n1p2)' [y/N] 
