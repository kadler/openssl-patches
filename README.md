# openssl-patches
IBM i specific OpenSSL patches

This repository contains a set of branches that correlate with a major OpenSSL release. Each branch contains a set of directories that correlate with an IBM i release and a directory ```any``` that applies to all IBM i releases.

The way to use this repository is:
- clone the branch specific to your version of OpenSSL
- copy the patches from ```any``` to the OpenSSL source directory
- copy the patches from the directory specific to your IBM i release to the OpenSSL source directory
- Apply each patch with ```patch -p1```

Example: Compiling OpenSSL 1.0.2h on IBM i 7.1

```
tar -xzf openssl-1.0.2h.tar.gz
git clone -b 1.0.2 --single-branch https://github.com/kadler/openssl-patches.git patches
cd openssl-1.0.2h
cp ../patches/any/*.patch .
cp ../patches/7.1/*.patch .
for f in *.patch
do
  patch -p1 < $f
done
```
