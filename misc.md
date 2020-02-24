
systctl -a --pattern 'randomize'
	three settings 0 -> disabled 1-> cautious 2-> full randomization
ldd /bin/bash => you can see different address space
sudo sysctl -w kernel.randomize_va_space=0 # disables the randomization

-Fpie -pie => Position indepentend execution flag
gcc -FPie -pie pie.c -i getAddr