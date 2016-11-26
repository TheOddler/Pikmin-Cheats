# Pikmin-Cheats

After many years I wanted to play Pikmin again, but I got very nervous having to deal with the time, so I decided to cheat a bit to relieve pressure.
I searched for some AR codes, but none were really to my liking.
I found one that should pause the time, but that didn't seem to work.
The author also stated that pausing the time causes Pikmin to be unable to break down walls and such, which isn't ideal.
So I decided to make my own.

To use, simply create a new AR code for Pikmin in Dolphin, and add the lines below as code.
Each cheat below must be a separate entry.
Also don't copy the explanation of what each line does, only copy the hexadecimal stuff.
The text after each hex instruction is just there for me and for others to learn from.

# The Cheats

Used adresses and the names I gave them:
* `<between balls>` has address `3A2924`.
It represents how far along between the current 2 balls you are on the time-line.
It seems to range from 0 to about 70 (float) when I look at it in the debugger.
* `<ball number>` has address `3A2930`.
It represents the current ball you are on on the time-line.
7 Is the first one for the day, above 7 is later in the day, below 7 is night (icon changes to a moon).

## Hold D-Pad Left to reverse time

```
CC3A2280 00010000       if D-Pad left is down execute all the following lines
843A2924 FFFDFC00           decrease <between balls> with a small number (negative version of the number used in the default advance time cheat for EU pikmin)
5C3A2924 41200000           if <between balls> is less than 10f do 2 lines
843A2930 FFFFFFFF               decrease <ball number> with 1
043A2924 42820000               set <between balls> to 65
```

## Hold D-Pad Right to advance time faster

```
0C3A2280 00020000       if D-Pad right is down execute 1 line
843A2924 00020400           increase <between balls> with a small number
```

## D-Pad Down to reset time

```
4C3A2280 00040000       if D-Pad down is down execute 2 lines
043A2930 00000007           set <ball number> to 7 (first of the day)
043A2924 40131E59           set <between balls> to something small
```

# Credits

Thanks to ResidentWaffle for his [noobs guide to AR coding](https://smashboards.com/threads/guide-to-ar-and-gecko-code-writing-for-complete-noobs.336650/).
