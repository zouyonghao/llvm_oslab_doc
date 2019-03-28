# BASIC DESCRIPTION

## LLVM

LLVM is a set of tools for compling, analizing, optimizing and building projects. You can get more infomation from [Official Website](http://llvm.org)

## What this project intend to do

In this project, you need to do a job which is similiar to optimizing code. You need to analyze the IR file and modified some code to meet the requirement.

This will need a basic understanding about LLVM Pass. A pass is a optimization job in LLVM optimization pipeline. When we get a IR file, the file will pipe to a pass sequence, each pass will do an optimization to your IR file.

```
original IR File --> pass1 --> pass2 --> ... --> optimized IR File
```

You can find some doc from the official website, and you'll find some tutorials about how to write a pass and use the tool ```opt``` to load this pass modual. But in this project, we'll finish this optimization job without ```opt```.

## Use the generator

It's hard to finish all code by yourself, because you need to know a little about ```cmake```. So, there is a generator for this kind of project.

```bash
sudo apt install npm
npm install -g yo
# if this step slow, you can try cnpm.
npm install -g generator-llvm
```

Now you can generator a project.

For example:
```bash
mkdir p1
cd p1
yo llvm:executable init
# then it will ask the project infomation
? Project name(p1)  [enter]
? Minimum required CMake version (3.4.3) [enter]
? LLVM install path. NOT the LLVM cmake module path (/usr/local/opt/llvm) /usr/lib/llvm-6.0
? New subdirectory name (llvm-p1)  [enter]
? Program name (llvm-p1) [enter]
? LLVM components that depends on(separated by commas) bitreader,bitwriter,interpreter,core,irreader,mcjit,native,option,support
```

Then you will get your project folder set.

```
.
├── CMakeLists.txt
└── llvm-p1
    ├── CMakeLists.txt
    └── main.cpp

1 directory, 3 files
```

Now, read the ```main.cpp``` and modified the code.

## Build

After finishing editing the code, you should build the project.

```bash
cmake -DCMAKE_BUILD_TYPE=DEBUG .
make
```

Then you'll get the executable file in the subdir you specified.

PS. This generator is not fully compitable with our project, I'll write one later.