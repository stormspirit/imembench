# imembench
Various in-memory storage systems exist today that offer similar functionality
but with different features (some more performant, others more reliable). Each
of the systems usually has its own APIs, making the benchmark results of them
often incomparable. The goal of *imembench* is to extract and create a common
wrapper of the interfaces exposed by these systems, and then drive these systems
with almost-the-same workloads by exercising this common interface. 

Implementation-wise, we need to use a common language that can talk to these
systems in the form of either the source language or bindings. 

## checkout repository:
after clone the main repository, run `git submodule update --init --recursive` to
pull the git submodules for building.

## build instruction:
TBA

## existing interfaces:
- RAMCloud:
  * `createTable(name)`
  * `dropTable(name)`
  * `getTableId(name)`
  * `read(tableId, key, keyLength, value, rejectRules, ...)`
  * `write(tableId, key, keyLength, buf, length, ...)`
  * `increment(tableId, key, keyLength, incrementValue, ...)`
  * `remove(tableId, key, keyLength, ...)`

- Tachyon (http://tachyon-project.org/api/java/index.html):
  * `int read()` 
  * `int read(byte[] b)`
  * `int read(byte[] b, int off, int len)`  
  * `void seek(long pos)`
  * `skip(long n)`
  *
  * `write(byte[] b)` 
  * `write(byte[] b, int off, int len)` 
  * `write(int b)` 
  * `flush()`
  *
  * `mkdir(TachyonURI path)`
  * `rename(TachyonURI srcPath, TachyonURI dstPath)` 
- Redis:
  * http://redis.io/commands

## existing languages:
- RAMCloud:
  * Source: C/C++
  * Bindings: Python, Java

- Tachyon:
  * Source: Java
  * Bindings: TBA

- Redis:
  * Source: C/C++
  * Bindings: C, C#, C++, Clojure, Common List, D, Dart, Elixir, emacs lisp,
    Erlang, Fancy, GNU Prolog, Go, Haskell, haXe, Io, Java, Lua, Matlab, Nimrod,
    Node.js, Objective-C, OCaml, Perl, PHP, Pure Data, Python, Rebol, Ruby,
    Rust, Scala, Scheme, Smalltalk, Tcl, VCL. (http://redis.io/clients)
