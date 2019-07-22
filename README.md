(Random musings of a madman follow)

# NextHawk Requirements

## All platforms supported by BizHawk
This is a no brainer.  No point in making a new thing if it's worse than the old thing.

## Separate cores as separate projects
One scalability problem BizHawk has is more or less requiring all cores to be part of the same repo and project.
The project gets too big and the maintenence burden gets too high.  It also gets hard to incorporate cores that have their
own established build methods and useful upstreams.
To solve this, we'll need a well defined, stable, core <-> frontend API.

## Subframe input scenarios
You can emulate a lot of systems pretty well without this, but eventually you absolutely need it for something,
and once you commit to it other cores that you force-fed into the frame based paradigm get better.

## Next-gen emulation
PCSX2, Cemu, RPCS3, Citra, Xenia, etc.  Some of them may be too complciated and too difficult to ever be cores,
but there should at least be the possibility, and nothing in the architecture should be holding them back.

## Portable, powerful UI toolkits.
I don't know the best way to write UI code.  But I know it's not C#+WinForms.  An emulator like BizHawk ends up having a lot
of complicated UI components in it, and they need to have a good foundation.

## Advanced debugging scenarios
This is one thing that keeps BizHawk from being the emulator of choice for some systems.  Complex TASing means complex
debugging.
Unfortunately, debugging can get very system-specific, and it might not be worth it to try abstracting a common API over
all debugging, but the foundation should be at least extensible enough so that individual system emulators can have
good debuggers written for them in NextHawk.

## Cores in many different languages, and frontend(s) in different languages too
Most cores are written in some sort of C/C++ flavor, but some aren't, and some that are use very esoteric
environments for the C/C++ (e.g. Waterbox).  A good UI toolkit is not likely to be
written in any C/C++ flavor.  These all have to work together.

## Frontend knowledge of advanced "GameInfo"
Understanding exactly what "ROM"s a run was made with is essential to reproducibility.
For systems where games were sold as single ROMs, and no extra metadata is needed, and a flat ROM
was adopted by the community as the standard format (e.g. GBA), this is pretty easy.
For optical disk systems, this is hard because optical disks suck.
For multi-rom arcade systems, this is hard because there's no standard combined format for them and
no standard database outside of what a specific emulator implements.
For JPC-RR... yeah.
We need to do what we can to harness the knowledge that individual emulators have (e.g. MAME) while still keeping
the frontend aware of what's going on.

