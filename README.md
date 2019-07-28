# javaenv

A Java version manager heavily inspired by rbenv and
[tfenv](https://github.com/tfutils/tfenv). `javaenv` manages
your installed Java versions and allow for keeping the Java version for a
project under version control.

## Support

javaenv currently only support Mac OS X but Linux support would be
straight-forward. Support for Windows should be doable but will require more
work.

## Installation

### Using git

```
$ git clone https://github.com/protocol7/javaenv.git ~/.javaenv

```

For convenience, add `javaenv` to your $PATH, e.g. using:

```
$ ln -s ~/.javaenv/javaenv /usr/local/bin
```

Shim the Java command line tools:

```
$ ln -nsf ~/.javaenv/javaenv /usr/local/bin/java
$ ln -nsf ~/.javaenv/javaenv /usr/local/bin/javac
...
```

This will allow you to automatically switch version for `java`, `javac` and
other tools, for example:

```
$ cat .javaversion
openjdk-11.0.2
$ javac -version
javac 11.0.2
```

## Usage

### Versions

Versions, as provided as command line arguments or in `.javaversion` files are
in the format of `<distribution>-<version>`. Supported distributions are:

* AdoptOpenJDK
* Amazon Corretto
* OpenJDK
* Oracle

A valid version would be, for example, `openjdk-11.0.2`.

The version can for some commands and for .javaversion files exclude the
distribution, in which case openjdk is used as the default. Thus, a valid
version can also be, for example, `11.0.2`.


### .javaversion

If a version is not provided for a command, or when calling Java command line
utilities, the version will be read from a file called `.javaversion` in the
current directory. This file should contain only the version, as defined above,
for example:

```
$ echo 'openjdk-11.0.2' > .javaversion
```

It is recommended that `.javaversion` is kept under version control with your
source code. This allows contributors to easily install and use the correct
Java version.

### javaenv install [version]

Install a version of the JDK. The version to install can either be provided to
the command, or read from a .javaversion file.

### javaenv uninstall version

Uninstall a specific version. The version must include the distribution name.

### javaenv list

List locally installed versions

### javaenv list-remote

List all versions available for installation.

### javaenv home [version]

Print the value for JAVA_HOME for the selected version. The version to install
can either be provided to the command, or read from a .javaversion file. The
command is useful when setting JAVA_HOME for tools using it, e.g. Maven.

```
$ export JAVA_HOME=$(javaenv home)
```

## TODO

  * Add support for automatically shimming Java command line tools
  * Add all released and still available versions
  * Add support for Linux
  * Add support for building Docker images
  * Add direct support for setting Java version for Maven
