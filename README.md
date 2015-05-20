# rainbowfy
Simple rainbow text effect suitable for 256-bit color ANSI terminal; particularly, for PS1 prompt. (Prints a lot of extraneous \['s)

Simple example usage (possibly in ~/.bashrc):

```
export PS1=$(rainbowfy $USER@$(hostname))":\w >\ [\033[0;00m\] "
```
