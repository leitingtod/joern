+++
title="Installation"
weight=1
+++

## Prerequisites

* Python3
  - Link: https://www.python.org/downloads/
* Java runtime 8
  - Link: http://openjdk.java.net/install/
* Scala build tool (sbt)
  - Link: https://www.scala-sbt.org/

Python3 and Java 8 are present in the official package repositories of
all major current Linux distributions and BSD flavors. For installing
the the Scala build tool (sbt), please following the instructions at:

https://www.scala-sbt.org/download.html

Any 1.x version of sbt works as sbt downloads the correct version for
building joern as part of the build process.

## Building the code

Once the dependencies are installed, run

```bash
git clone https://github.com/ShiftLeftSecurity/joern.git
cd joern
sbt stage
```

This builds the Joern Java library and Joern server.

## A Test Run

To test if the build was successful, you can run
```
./joern-parse joern-cli/src/test/resources/testcode/free
```
This command will create a code property graph for the sample program in the directory `src/test/resources/testcode/free`, and store the graph in the file `cpg.bin.zip`.

## Configuring the JVM for Optimal Performance

Code analysis can require lots of memory, and unfortunately, the JVM does not pick up the available amount of memory by itself. While tuning Java memory usage is a discipline in its own right, it is usually sufficient to specify the maximum available amount of heap memory using the JVM's -Xmx flag. The easiest way to achieve this globally is by setting the environment variable _JAVA_OPTS as follows:

```
export _JAVA_OPTS="-Xmx$NG"
```

where $N is the amount of memory in gigabytes. You can add this line to your shell startup script, e.g., ~/.bashrc or ~/.zshrc.

# Installing the Python interface

Joern can be scripted using the local REST API. The Python 3 library `cpgclientlib` serves as a reference implementation for a CPG client library, and enables scripting of Joern with Python. The library can be installed as follows.


```
pip install cpgclientlib
```

Documentation on `cpgclientlib` is available at:
https://github.com/ShiftLeftSecurity/codepropertygraph/tree/master/cpgclientlib
