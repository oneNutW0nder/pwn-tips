# pwn-tips
Tips and tricks that I come across and need to remember for exploitation.

## Pwntools -- Tips for working with Pwntools

- Setup a dedicated _pwn_ box where you write your exploits. 
  - This is because Python is toxic and you need a stable env for doing this stuff.

- When using python3 make sure everything is defined as a _byte string_

- After creating a payload, remove any null-bytes if they exist and adjust padding as necessary

## Misc -- Miscellaneous tips about exploitation

- When testing code redirection/exectution throw in a SIGTRAP `\xcc`
  - When testing the exploit now you will know if you have control if the program exits with SIGTRAP status
  - This allows validation without stepping through a debugger or trying to attach

- Getting around bad characters:
  - To get around bad characters like null-bytes and newlines you can craft the values if you have space for the shellcode
  - Example (_my shellcode for heap0 phoenix_):
    ```assembly
    xor eax, eax
    mov ax, 0x40
    shl eax, 0x10
    mov ax, 0x0abd
    jmp eax
    ```
  - This builds the addres `0x400abd` which has a newline byte in it and using an instruction such as `mov eax` would not work either due to `mov eax` introducing null bytes.

- Keep in mind potential code segments that could be used to leak addresses. (_example in pwnable.tw/start_)

- Leaking libc addresses with ROP:
  - https://book.hacktricks.xyz/exploiting/linux-exploiting-basic-esp/rop-leaking-libc-address
