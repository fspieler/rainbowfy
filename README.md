# rainbowfy
Simple rainbow text effect suitable for 256-bit color ANSI terminal; particularly, for PS1 prompt. (Prints a lot of extraneous \['s)

Simple example usage (possibly in ~/.bashrc):

```
export PS1=$(rainbowfy $USER@$(hostname))":\w >\ [\033[0;00m\] "
```
 Explanation of how it works:
 
I owe credit to a blog post that I can't find at the moment, which described how to create a rainbow effect: basically, vary the R,G,B components as 120 deg out-of-phase sine waves.

The ANSI colorscheme is 256-bit, but the values for 0-15 and 232-255 are special values. R,G,B have six possible values 0-5. The `convertColor` function will form a color value in the range 15-231 from component RGB values.

The `indexes` array varies sinusoidally between 0 and 5 and back. Iterating over that array is like iterating over a low-res digitally sampled sine wave. In order to get "120 deg out-of-phase" sine waves, the indexes of RGB need to be evenly spaced over that array.

The period of the rainbow effect is the length of `indexes`. In order to shorten the period and get a larger effect, you can step through the array by more than one index at a time. This corresponds to the `factor` parameter to `colorizeString()`.
