# hakchi2

This application can add more games to [the Nintendo Classic Mini: NES](https://www.nintendo.co.uk/Misc-/Nintendo-Classic-Mini-Nintendo-Entertainment-System/Nintendo-Classic-Mini-Nintendo-Entertainment-System-1124287.html) or [the Nintendo Classic Mini: Famicom](https://www.nintendo.co.jp/clv). All you need to do is connect it to a Windows PC via Micro-USB cable. No soldering, no disassembling.

### Features
* Change any game settings (including command-line arguments)
* Fill all game data automatically using included database
* Automatically check for supported games
* Search for box art using Google Images
* Use [Game Genie](https://en.wikipedia.org/wiki/Game_Genie) codes
* Automatically patch problem games (patches for many popular games included)
* Upload hundreds of games at once
* Return to the HOME menu with a button combination instead of the Reset button
* Enable autofire A/B
* Simulate the start button on the second controller (for Famicom Mini)
* Disable seizure protection
* Disable HOME menu music

## So did you hack the NES Mini?
No! It was my Russian сomrade [madmonkey](https://github.com/madmonkey1907). He created the original [hakchi](https://github.com/madmonkey1907/hakchi) tool. It was not very user-friendly, so I created a tool that would be simple for everyone, not only Linux users. I named it “hakchi2” because I don’t like coming up with names. This resulted in the first version being 2.0 :)

## How do I use it?
You just need to unpack it somewhere (installation not required), run it, press “Add more games”, select some ROMs and press “Synchronize”. The application will guide you.

## How does it work?
You don’t need to worry about it. But if you really want to know it’s using [FEL mode](http://linux-sunxi.org/FEL). FEL is a low-level subroutine contained in the [BootROM](http://linux-sunxi.org/BROM) on [Allwinner](https://en.wikipedia.org/wiki/Allwinner_Technology) devices. It is used for initial programming and recovery of devices over USB.

This allows us to upload code into RAM and execute it. In this way we can read the Linux kernel (yes, the NES Mini runs on Linux), write the kernel or execute the kernel from memory without writing it to flash. We can dump the kernel image of the NES Mini, unpack it, add some games and a script which will copy them to flash, repack, upload and execute.

The games directory is on the read-only partition, so we also need to create and flash a custom kernel with a special script that creates a sandbox folder on the writable partition and mounts it over the original games folder. So your original files are safe. You can’t delete or harm the original files in any way. For kernel patching, hakchi2 is just executing other applications, that’s why there is the “tools” folder.
