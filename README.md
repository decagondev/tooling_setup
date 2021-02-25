# Tooling Setup

# Cross C Compiler and toolchain

## Cross Compiler Bin setup in linux

- make a dir to put the files in
- cd in to that dir
- wget the zip file
- unzip the files
- edit your profile to add the bin folder to path


### Make Directory
```
mkdir ~/.cross
```

### Change Directory
```
cd ~/.cross
```

### WGET Files
```
wget https://github.com/lordmilko/i686-elf-tools/releases/download/7.1.0/i686-elf-tools-linux.zip
```

### unzip Files
```
unzip i686-elf-tools-linux.zip
```

### edit Profile
- open editor

```
vim ~/.profile
```

- add this to the end of the Profile

```
; if the directory exists add it to the path
if [ -d "$HOME/.cross" ] ; then
    PATH="$HOME/.cross:$PATH"
fi

; if the directory exists add it to the path
if [ -d "$HOME/.cross/bin" ] ; then
    PATH="$HOME/.cross/bin:$PATH"
fi
```

### Testing it works

- Run the gcc and get the version

```
i686-elf-gcc --version
```

- make a new freestanding c file

```
vim myfile.c
```

- add some c code

```C
int main() {
    return 0;
}
```

- make a new Makefile

```
vim Makefile
```

- add a target to the makefile

```
myfile.o: myfile.c
    i686-elf-gcc -c myfile.c --freestanding -o myfile.o
```

- run a make

```
make myfile.o
```
