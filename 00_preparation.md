# PREPARATION

## Get the code

Get some projects(AddToSub) from your colleagues

## Install

```bash
sudo apt install llvm-6.0
sudo apt install llvm-6.0-doc
sudo apt install clang
sudo apt install cmake
```

## Build

```bash
cd AddToSub
cmake .
make
```

If you got an error ```ld cannot find -lz```, do this

```bash
sudo apt install zlib1g-dev
```

Then try ```make``` again

## Test

### Test the original file

```bash
clang test.cpp
./a.out
```
Then the output should be
```
c = 3
d = 5
```

### Test the modified program

```bash
clang -S -emit-llvm test.cpp # you get test.ll
./src/AddToSub test.ll # you get test_result.ll

clang test_result.ll
./a.out
```

Or just use ```lli```

```bash
sudo apt install llvm-runtime
lli test_result.ll
```



Then if you get

```bash
c = -1
d = -3
```

You have finished the preparation for next step.
