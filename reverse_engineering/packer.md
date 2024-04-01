# Packer
![packer](https://github.com/fzkn4/PicoCTF-2024/assets/147215607/b5077559-1171-41e4-b48a-740a0f872710)

This challenge is about `packing executables`. What this means is that when executable file is packed, the executable code is `compressed`. means code can be modified without changing the function of the file. Packed files are a great way to save space and secure files. Packing executable file helps `reduce the size` of files and `protects them against reverse engineering`.
#
I tried looking what's inside the binary file using `Ghidra`, and found an information on how to solve the problem:
![packer_pic1](https://github.com/fzkn4/PicoCTF-2024/assets/147215607/94167213-7f56-4077-9ea0-8055081b1748)

The binary file was packed using UPX packer. 
#

`UPX` is the command-line tool an advanced executable file compressor. typically reduce file size by 50 to 70%. Reduce file size means less disk consumption, network load times. this tool can be used for packing and unpacking executable file. 

Some of the useful UPX commands are:

`$upx -9 filename.exe ( to pack/compress the file )`

`$upx -d filename.exe ( to unpack/decompress the file ) `
#
> Unpacking using UPX

I used the command: 

`$ upx -d out -o output`

This will `unpack/decompress` the file and save the `output` on the same directory.

After that, let's take a look at what's inside `output` using Ghidra:

![packer_pic3](https://github.com/fzkn4/PicoCTF-2024/assets/147215607/8cd17301-421c-4b4b-9fa7-6d878b5c9e9e)

Here we can see in the `main` function `line 66` says:

`"Password correct, please see flag: 7069636f4354467b5539585f556e5034636b314e365f42316e345269 33535f65313930633366337d"` 

`Unhex` the output and it should give you the flag.
#
Flag: `picoCTF{U9X_UnP4ck1N6_B1n4Ri3S_e190c3f3}`
