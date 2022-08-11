## Compiler wrapper for Facebook Infer

A script that wraps C/C++ compilers to capture the compilation commands that
are used to run the capture phase of Infer.

### Usage
Clone the repository:

```
git clone https://github.com/TomasBeranek/infer-compiler-wrapper
cd infer-compiler-wrapper
```

Make sure the wrapper is executable:

```
sudo chmod +x wrapper
```

On [line 4](https://github.com/TomasBeranek/infer-compiler-wrapper/blob/b7a2dc5150db45a650050299870d824e0a8d1267/wrapper#L4), add the name of the compiler, e.g. for ```gcc``` the line should
look like this:

```
compiler="gcc"
```

Replace the compiler with the wrapper and rename the compiler to
[COMPILER]-original, e.g. for ```gcc```:

```
sudo mv /usr/bin/gcc /usr/bin/gcc-original
sudo cp wrapper /usr/bin/gcc
```

Compile the analyzed project. **Source files that are not compiled will not be
captured and therefore not analyzed!**

Captured files are stored in ```/tmp/infer-out``` by default.

Finally, run the analysis, e.g.:

```
infer analyze --pulse --bufferoverrun -o /tmp/infer-out
```
