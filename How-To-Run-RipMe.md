Make sure you have Java installed. You can download / install it at this site: http://www.java.com/en/download/help/index_installing.xml

The `ripme.jar` file is actually executable. Java will execute the `.jar` file similarly to how `.exe` files are executed. Usually double-clicking the `.jar` file executes the program.

If double-clicking the `.jar` file does not open the program, you can right-click the file and select an `Open With...` option, then select the `Java` runtime application.

If all else fails, you can run the program via command-line by navigating to the directory and executing
```bash
java -jar ripme.jar
```

Command Line Options
--------------------
```
﻿usage: java -jar ripme.jar [OPTIONS]
 -h,--help            Print the help
 -r,--rerip           Re-rip all ripped albums
 -t,--threads <arg>   Number of download threads per rip
 -u,--url <arg>       URL of album to rip
 -w,--overwrite       Overwrite existing files
```

## Docker

[Docker](https://hub.docker.com/r/kastang/ripme) for deploying an environment suitable to run RipMe by [@JoshKastang](https://github.com/JoshKastang) ([#469](https://github.com/4pr0n/ripme/issues/469))