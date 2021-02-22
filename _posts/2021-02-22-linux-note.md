---
title: "Linux Notes"
excerpt_separator: "<!--more-->"
categories:
  - Tech
classes: wide

---

- cmake
  - `which cmake` to see where is the cmake
  - `/usr/lib/cmake/` contains part of packages built.
  - For many packages, when installed, they automatically have `.cmake` file under the cmake folder, therefore cmake can easily find them.
  - For some packages, by `sudo apt-get install` cannot generate `.cmake` files, so we need to install them from source.
  - `cmake` will search the library stored under:
    - `/usr/local/lib/cmake`
    - `/usr/lib/cmake`

- file permission
  - to list all links in the current folder: `find . -type l -ls`
  - Green background, blue fonts means everyone has write permission.
  - To check the write/read permission: `ls -l`.







