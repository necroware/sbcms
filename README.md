# CMS Logic Scheme for Sound Blaster 2.0

The final revision of the original Sound Blaster, the *Sound Blaster 2.0* was
released in October 1991. It supported two kinds of synthesizers *OPL2 (Adlib)*
and *Creative Music System (CMS)*, which used the same technology as various
gaming consoles and personal computers of that time. There were not many games,
which supported CMS, however there were some very famous among them, like *Monkey
Island*. We all know from back in the days how OPL2/3 sounds like, but if you
also always wanted to know how CMS sounds like, you have to buy an old Creative
Sound Blaster 1.0, 1.5 or 2.0. Unfortunately as soon as OPL2 found its way to
the sound cards of that time, CMS died quickly. Where the Sound Blaster 1.0 had
CMS always on board, the version 1.5 already made it optional and a lot of cards
came only with DIP sockets for the CMS synths but without chips. For Sound
Blaster 2.0 it got even worse, not only the synth chips were removed, but also
the logic IC to control them. Today most of the old dusty Sound Blaster 1.5/2.0
cards you can buy are coming without the named chips. For Sound Blaster 1.5 this
is not a problem at all, since you can buy two *Phillips SAA-1099* synthesizer
chips and put them into the DIP sockets. However, for Sound Blaster 2.0 you
need the logic IC, where this project comes into play.

## Where is the code comming from

It is almost impossible to find the original CMS chips made by Creative anymore.
In the year 2011 the code for the logic chip was published on
[vogons.org](https://www.vogons.org/viewtopic.php?f=5&t=30242), but quite fast
it was clear, that it doesn't work on all revisions of the Sound Blaster 2.0
cards. Some people tried to resolve the issues, but without a success. At least
until 2018, where one guy named `suntac` reported, that he reverse engineered
the hardware and found a solution. He had his honorable reasons not to open the
code to the community, but at least he was so kind to provide the chips for a
little fee. However, as a friend of open source, I wanted to make the solution
available for everyone.  Thankfully to `suntac`, I knew now, that a solution
does exist, so I decided to try to reverse engineer it on my own. This project
is the result of my work.

**ATTENTION:** I don't give any kind of warranty, nor guaranty. This procedure
could break your hardware and I take no responsibility for your actions, so 
use it at your own risk.

## What you need

As for Sound Blaster 1.5 you will need two Phillips SAA-1099 synthesizer
chips, which you can buy on the internet for a little money. Additionally
you will need programmable array logic IC or short PAL, model GAL16V8. They
are also very cheap and can be found on the internet. If you buy the ICs
buy couple more, than you need. You never know, but sometimes they get
broken too fast. Additionally, you will need a programmer to burn the
logic to the PAL. You can use TL866 or something similar. Regarding software,
you'll need an old DOS tool called EQN2JED to compile the source code. If
you work on linux, EQN2JED runs in the DosBox flawlessly.

## How to revive CMS on your Sound Blaster 2.0

First of all compile the equation sbcms.eqn file using EQN2JED. You should
see no error on the output and a new file in the same directory named SBCMS.JED
should appear. This binary file you will need to burn to the PAL. This step
is very much dependent from the IC programmer you have, so just follow the
documentation for you programmer. If you burned the JED to the PAL, you are
almost done, just put the SAA-1099 chips and the PAL to your sound card, remove
the jumper CMSOFF (which disables CMS) and turn on your PC.

## How to test

First of all, do your test with any DOS game, which supports OPL2 (or Adlib).
Make sure, that the autodetect of the sound card works as expected. If it runs
well, try a game with CMS support. For example, you can use Monkey Island by
running with argument `g` to run with CMS or with argument `a` to run with OPL2
support.

## Troubleshooting

There are many different revisions of the Sound Blaster 2.0 out there and the
provided logic code may be incompatible to some of them. If your OPL2 sound
doesn't work, you can try to find out if at least CMS is working, vice versa.
If the sound is crap (more than usual), nothing works or whatever, it is not
sufficient to just put back the CMSOFF jumper back, you have to remove all the
installed chips either.

## Tested hardware
- Sound Blaster 2.0 CT1350B revision 069328 (with CT1336A)

## Special thanks

I want to thank `suntac` for his valueable support in reviewing my solution and
sharing his experience. He was the first one, who was able to crack the nut and
without knowing that, I probably wouldn't try to solve the problem myself.
Meanwhile he also opened his work to the world, which you can find on 
[vogons.org](https://www.vogons.org/viewtopic.php?f=5&t=66361)

