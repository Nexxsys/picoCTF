# picoCTF Write Ups

## General Skills
### Obedient Cat

**Description:** This file has a flag in plain sight (aka "in-the-clear"). Download flag.

In a Webshell session:
```bash
wget https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag
cat flag
```
Result: 
```bash
picoCTF{s4n1ty_v3r1f13d_1a94e0f9}
```

### Wave a flag

**Description:** Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...

```bash
wget https://mercury.picoctf.net/static/beec4f433e5ee5bfcd71bba8d5863faf/warm
file warm
```
Result:
```bash
warm: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=506b7be935d8940c672ab0d40d2e03ebd746155b, with debug_info, not stripped
```
one of the hints is this: This program will only work in the webshell or another Linux computer.

This would mean that it is a an executable file. Lets check the permissions on this file:
```bash
ls -al
```
Result:
```bash
-rw-rw-r-- 1 nexxsys-picoctf nexxsys-picoctf 10936 Mar 16 01:04 warm
```
As we can see there is no execution permissions on the file.  Lets chmod it:
```bash
chmod +x warm
```
Result:
```bash
-rwxrwxr-x 1 nexxsys-picoctf nexxsys-picoctf 10936 Mar 16 01:04 warm
```
Now we need to execute the file
```bash
./warm
```
The result isn't exactly what we expected:
```bash
Hello user! Pass me a -h to learn what I can do!
```
Re-run with the **-h** option:
```bash
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_616f7182}
```
Success!!

