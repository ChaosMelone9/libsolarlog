# libsolarlog
[![Build Status](https://github.com/ChaosMelone9/libsolarlog/actions/workflows/maven.yml/badge.svg)](https://github.com/ChaosMelone9/libsolarlog/actions/workflows/maven.yml)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)


Hello everyone, and thank you for checking out this little project. This library is for reading data and converting it from the backup files generated by your SolarLog.

The goal is to keep a modular way to easily read and manipulate the data to be able to work with it in other projects.

If you want to improve some functions or contribute feel free to do so, also feel free to use this project in any way that could help you personally.

Greetings, ChaosMelone9
(Sorry for the lack of english skills :P )

## Features

- Read from .js-files
- Download from FTP-Server
- Upload to MariaDB

## How to use

This will guide you through a very basic process of being able to use data for your own.

### Importing

Sadly this project is not hosted anywhere (yet), so you have to import it on your own. I'll assume you use Maven for this case, steps for other platforms or IDEs are well documented in the internet. To import type the following:

```
#!/usr/bin/bash
export version=0.0.2
#If you haven't downloaded the binary run the following:
wget "https://github.com/ChaosMelone9/libsolarlog/releases/download/$version/libsolarlog-$version.jar"

#Run this to install into your local repository
mvn install:install-file -Dfile=libsolarlog-$version.jar -DgroupId=com.github.chaosmelone9 -DartifactId=libsolarlog -Dversion=$version -Dpackaging=jar
```

Now it is installed in your local repository, and you are free to add it as a dependency for your project.
Simply drop this in your pom.xml:

```xml
<dependency>
    <groupId>com.github.chaosmelone9</groupId>
    <artifactId>libsolarlog</artifactId>
    <version>0.0.2</version>
</dependency>
```

### Usage

This project is structured around the SolarMap object. You can easily add data to it and retrieve from it.

Here's an example:

```java
import com.github.chaosmelone9.libsolarlog.SolarMap;

import java.io.File;
import java.util.Date;
import java.util.List;
import java.util.Map;


public class Class {
    public static void main(String[] args) {
        SolarMap solarMap = new SolarMap();
        
        solarMap.addFromFTPServer("host", "user", "password");

        solarMap.pushToMariaDB("user", "password", "address", "database", true);
    }
}
```
