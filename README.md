# pwn-tips
Tips and tricks that I come across and need to remember for exploitation.

## Pwntools -- Tips for working with Pwntools

- Setup a dedicated _pwn_ box where you write your exploits. 
  - This is because Python is toxic and you need a stable env for doing this stuff.

## Misc -- Miscellaneous tips about exploitation
- When testing code redirection/exectution throw in a SIGTRAP `\xcc`
  - When testing the exploit now you will know if you have control if the program exits with SIGTRAP status
  - This allows validation without stepping through a debugger or trying to attach

