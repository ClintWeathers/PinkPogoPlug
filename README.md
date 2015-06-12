# PinkPogoPlug
Just some information about getting Debian Wheezy on a Pink Pogoplug.  

[Source](http://fzr.squeenus.com/debian/ "Permalink to FZR's Very Dull PogoPlug Running Debian Linux Script Page")

# FZR's Very Dull PogoPlug Running Debian Linux Script Page

It uses embedded linux, IP tunnelling and zero-configuration networking to give you a very slick and easy to use NAS (network accessible storage) unit. One could host and share photos, music, movies, etc on this and never want for anything more.

Sadly, I'm not one of those people. I found the interface clunky and I just grated at only being able to have one user on the PogoPlug. What I really wanted was Linux.

_Just a note: The stuff I'm talking about below -- it can brick your PogoPlug, rendering it absolutely useless for anything other than a doorstop or fuel for a fission reactor. Seriously, if you really like your PogoPlug and aren't willing to risk having it bricked, just keep it as-is. _

"You've been warned" he said, in an ominous voice.

The very minute I had this thing up and running, I was immediately googling for "hacking pogoplug" and came across both PlugboxLinux which I cannot recommend to experienced linux users because it will give you migraines. However, Plugbox Linux is just peachy for new linux users for one standout reason: There is very little that can go wrong with a PlugLinux install (the danger is all in the NAND flashing) and you can do some swell things with it.

But, I'm not a new linux user (nor am I [a sysadmin by trade][1], just an analyst whose job is greatly buffed by having an MCSE and CNA in a former life) so there are things I need in a linux distribution to be happy: A package manager, close mirrors, never ever ever having to use vi (UPDATED: Ok, I actually like vi and vim now. Emacs still sucks), etc. We all have our preferences in life.

So with more digging, I came across [Jeff Doozan's implementation of Debian linux for the PogoPlug][2] (as well as Dockstar and other similar Marvell-based NAS devices). He also figured out a way to hack the PogoPlug firmware to keep it from autoupdating. This is important because any phone-home from the PogoPlug back to the mothership could result in a firmware update that would lock you out of it, and make the PogoPlug just a nice pink NAS device instead of the little bit of awesome that it can be.

And one might ask, "Just what kind of bits of awesome do you describe?"

Let me list a few:

* Shoutcast server for setting up your own internet radio station
* Firefly server for streaming out your own music anywhere
* Hosting and sharing your own photos, videos, files, etc. without having to pay Flickr
* Samba (aka windows file sharing) server
* Calibre e-book server (see link below for FAQ on getting it set up)
* Having your own WebDAV server do you don't have to pay Dropbox to get your files anywhere
* A great, nearly bulletproof box on which to learn linux, system administration, SQL, networking, Perl (or any other scripting language)

In addition, he also wrote a [brand new firmware][3] for it that is greatly improved as a "rescue system" but I think in time it will evolve into a useable firmware on its own.

In additon, Peter Gunn has written some [very nice bash scripts][4] to handle some of the post-install configuration. On top of that, he is very willing to give advice to us Pogoplug hackers on the forum.

So how, one might ask, did these scripts come to live on Squeenus? Certainly not by any skill on my part.

I didn't write a damned one of these and sadly, can take neither credit nor blame. My *nix skills pale to theirs and I stand on their shoulders.

I put them here because jeff.doozan.com gets busy at times and can time out on a wget request. Much respect to him for writing and hosting the dockstar debian installer and to Peter for writing the setup scripts. And also to put them somewhere with my own notes for configuration later. Because I have this odious habit of blasting systems and starting from scratch. Poor form, I know. But I'm not in a production environment, so phbbt.

A couple of notes. Please pay attention to these as they could bite you in the ass: I did change the default mirror on the dockstar install to be http://punk.uchicago.edu/debian since cdn.debian.net sends you to a random mirror, many of which suck. I had errors ranging from packages.gz being corrupt to timeouts to mirrors which gave random 401's and 404's on packages. Very frustrating.

If you're reading this, then I'm quite sure it goes without saying that you are able to (and well should) change the DEB_MIRROR to one geographically close to you for best results. Temper that with finding a mirror that does not suck.

In setup packages script, I removed the fastest-repository finder as the fastest frequently ended up being, well, mirrors that suck.

Your mileage, naturally, may vary.

As someone who admires small, elegant tech -- from the wristwatch to the Pogoplug -- I wish you the very best of luck with your embedded linuces, microservers and nand flashings.

A couple of notes, mostly for my own reference:

* nano and dialog should be installed right away. Nano is a text editor and a blessing if you wish to avoid the horror that is vi and Emacs. And if you're not used to either of those, you should install Nano. It's pretty easy to use. Dialog is a framework for asking you what options you want during software installs, and without it you frequently get Hobson's choice.
* I'm sure I'll think of more as I see them.
* I did think of one afterall: If you are using a pink PogoPlug, do yourself a huge favor and install Jeff's rescue system. It basically replaces the PogoPlug firmware altogether with a much, much more useable system. But again, bewarned that all flash updates carry a risk of bricking your PogoPlug.

Good hunting,

-FZR

**_The files:_**

[dockstar.debian-squeeze.sh (the script that installs debian on the pogoplug)][5]  
The script has been changed to point to punk.chicago.edu as the mirror rather than the Canadian mirrors which sometimes suck.

**This is the updated part**

If you want to use the Wheezy version of Debian, then use this script instead:  
[dockstar.debian-wheezy.sh][6]

The main advantage for me (and a few of you) of Wheezy is that Calibre (the ebook server) is now available as an apt-get package in Wheezy.  
Also, I've added sudo and apt-utils to the list of packages installed in the script. Also, it should install the 3.1* version of the linux kernel.  
**After this, mostly not so updated. Except the postscript.**

[Peter Gunn's package setup script (with the repository search commented out)][7] This installs a cubic buttload of scripts and may not be good for you if you have a really small (say, less than 4 gig) thumbdrive as your /dev/sda.

[Installs Gorgone's updated kernel. ][8] Not sure what it does, frankly. Haven't had time to check.

[Peter Gunn's script to set up OpenVPN. This is truly nifty.][9]  
Here is a [Mac OSX client for OpenVPN][10]  
Unfortunately as of yet (Jan 2012) there is still not OpenVPN app for iOS devices (grumble grumble).

**_A Few More Things, Mostly For My Own Pea Brain_**

* [A good tutorial on how to set up a LAMP server in Debian.][11] Follow this just like it says and you'll be up and running in no time. While you're doing your MySQL install, after the install be sure to run [mysql_secure_installation][12] and it'll wire it down a bit tighter.

[1]: http://3.bp.blogspot.com/_rwn0c_rQpIU/SMXb7IJD9EI/AAAAAAAAAIo/d-w0Jb9xWCY/s400/neckbeard.jpg
[2]: http://jeff.doozan.com/debian/
[3]: http://forum.doozan.com/read.php?4,831
[4]: http://jeff.doozan.com/debian/lcd/
[5]: http://fzr.squeenus.com/debian/dockstar.debian-squeeze.sh
[6]: http://fzr.squeenus.com/debian/dockstar.debian-wheezy.sh
[7]: http://fzr.squeenus.com/debian/setup_packages.sh
[8]: http://fzr.squeenus.com/debian/setup_kernel.sh
[9]: http://fzr.squeenus.com/debian/setup_vpn.sh
[10]: http://code.google.com/p/tunnelblick/
[11]: http://wiki.debian.org/LaMp
[12]: http://www.mysql-optimization.com/mysql-secure-installation-program.html
