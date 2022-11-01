### Welcome to litecoinj

This Java library for Litecoin is a fork of bitcoinj

The litecoinj library is a Java implementation of the Litecoin protocol, which allows it to maintain a wallet and send/receive transactions without needing a local copy of Litecoin Core. It comes with full documentation and some example apps showing how to use it.

### Technologies

* Java 8+ (needs Java 8 API or Android 6.0 API, compiles to Java 8 bytecode) and Gradle 4.4+ for the `core` module
* Java 8+ and Gradle 4.4+ for `tools` and `examples`
* Java 11+ and Gradle 4.10+ for the JavaFX-based `wallettemplate`
* [Gradle](https://gradle.org/) - for building the project
* [Google Protocol Buffers](https://github.com/google/protobuf) - for use with serialization and hardware communications

### Getting started

To get started, it is best to have the latest JDK and Gradle installed. The HEAD of the `master` branch contains the latest development code and various production releases are provided on feature branches.

#### Building from the command line

Official builds are currently using with JDK 8, even though the `core` module is compatible with JDK 7 and later.

To perform a full build (*including* JavaDocs and unit/integration *tests*) use JDK 8+
```
gradle clean build
```
If you are running JDK 11 or later and Gradle 4.10 or later, the build will automatically include the JavaFX-based `wallettemplate` module. The outputs are under the `build` directory.

To perform a full build *without* unit/integration *tests* use:
```
gradle clean assemble
```

#### Building from an IDE

Alternatively, just import the project using your IDE. [IntelliJ](http://www.jetbrains.com/idea/download/) has Gradle integration built-in and has a free Community Edition. Simply use `File | New | Project from Existing Sources` and locate the `build.gradle` in the root of the cloned project source tree.

### Building and Using the Wallet Tool

The **litecoinj** `tools` subproject includes a command-line Wallet Tool (`wallet-tool`) that can be used to create and manage **litecoinj**-based wallets (both the HD keychain and SPV blockchain state.) Using `wallet-tool` on Litecoin's test net is a great way to learn about Litecoin and **litecoinj**.

To build an executable shell script that runs the command-line Wallet Tool, use:
```
gradle litecoinj-tools:installDist
```

You can now run the `wallet-tool` without parameters to get help on its operation:
```
./tools/build/install/wallet-tool/bin/wallet-tool
```

To create a test net wallet file in `~/litecoinj/litecoinj-test.wallet`, you would use:
```
mkdir ~/litecoinj
```
```
./tools/build/install/wallet-tool/bin/wallet-tool --net=TEST --wallet=$HOME/litecoinj/litecoinj-test.wallet create
```

To sync the newly created wallet in `~/litecoinj/litecoinj-test.wallet` with the test net, you would use:
```
./tools/build/install/wallet-tool/bin/wallet-tool --net=TEST --wallet=$HOME/litecoinj/litecoinj-test.wallet sync
```

To dump the state of the wallet in `~/litecoinj/litecoinj-test.wallet` with the test net, you would use:
```
./tools/build/install/wallet-tool/bin/wallet-tool --net=TEST --wallet=$HOME/litecoinj/litecoinj-test.wallet dump
```

Note: These instructions are for macOS/Linux, for Windows use the `tools/build/install/wallet-tool/bin/wallet-tool.bat` batch file with the equivalent Windows command-line commands and options.

### Example applications

These are found in the `examples` module.

### Where next?

Now you are ready to [follow the tutorial](https://bitcoinj.github.io/getting-started).

### Testing a SNAPSHOT build

Building apps with official releases of **bitcoinj** is covered in the [tutorial](https://bitcoinj.github.io/getting-started).

### Notes

build.gradle: Migrate from maven to maven-publish plugin

To publish to the local Maven repository, use `gradle publishToMavenLocal` rather than `gradle install`.