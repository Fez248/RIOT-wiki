Okay, there are a lot of different ways, first I am trying using [FirmAE](https://github.com/pr0v3rbs/FirmAE).

Go check their GitHub for installation and instructions.

It didn't work. I am trying something which is not literally hardware emulation but maybe it works for me:

```bash
sudo apt-get update
sudo apt-get install -y qemu-user-static
```

Copy the emulator into the extracted filesystem's usr/bin directory:

```bash
sudo cp /usr/bin/qemu-mipsel-static ./usr/bin/
```

Chroot into the extracted filesystem:

```bash
sudo chroot . /bin/sh
```

Didn't work either. So I tried [Firmadyne](https://github.com/firmadyne/firmadyne) which was the most successfull one. It manage to start the booting process but if failed due to some error I don't yet know how to solve.

Thankfully with our clients we won't need to do this as either we will be able to emulate it with their support if they have internal emulators, or we will ask for a real device to test on. Nevertheless, it is probably not even needed to emulate to know that libcrypto being outdated is a  thread, specially connected to httpd. I can try attacking it on my real router however I dont know if its the same hardware neither how does httpd use libcrypto and if I can trigger the vulnerable function so it will be a little bit going blind.

I will try a little bit, however it's not fully needed to suceed, even if I wanted to. I can still keep looking for other CVEs or even analyze the web folder where the portal resides and more user level things... I guess, I'll see, but its still really good progress for the company all the knowledge gained here.