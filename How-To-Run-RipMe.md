Make sure you have Java installed. You can download / install it at this site: http://www.java.com/en/download/help/index_installing.xml

The `ripme.jar` file is actually executable. Java will execute the `.jar` file similarly to how `.exe` files are executed. Usually double-clicking the `.jar` file executes the program.

If double-clicking the `.jar` file does not open the program, you can right-click the file and select an `Open With...` option, then select the `Java` runtime application.

If all else fails, you can run the program via command-line by navigating to the directory and executing
```bash
java -jar ripme.jar
```

By default ripme will store all it's config and history files in the users config folder (LOCALAPPDATA/ripme for windows, ~/.config/ripme for linux, ~/Library/Application Support/ripme for MacOS). To over ride this behaviour and have ripme store all it's config and history files in the same folder as ripme.jar create a file named rip.properties in the same folder as the jar and then start ripme

Command Line Options
--------------------
```
﻿usage: java -jar ripme.jar [OPTIONS]
 -h,--help                  Print the help
 -4,--skip404               Don't retry after a 404 (not found) error
 -d,--saveorder             Save the order of images in album
 -D,--nosaveorder           Don't save order of images
 -f,--urls-file <arg>       Rip URLs from a file.
 -h,--help                  Print the help
 -l,--ripsdirectory <arg>   Rips Directory (Default: ./rips)
 -n,--no-prop-file          Do not create properties file.
 -r,--rerip                 Re-rip all ripped albums
 -R,--rerip-selected        Re-rip all selected albums
 -t,--threads <arg>         Number of download threads per rip
 -u,--url <arg>             URL of album to rip
 -v,--version               Show current version
 -w,--overwrite             Overwrite existing files
 -s,--socks-server          Use socks server ([user:password]@host[:port])
 -p,--proxy-server          Use HTTP Proxy server ([user:password]@host[:port])
 -j,--update                Update ripme
 -a,--append-to-folder      Append a string to the output folder name
 -H,--history               Set the path of the history file. EX: -H /path/to/history.txt
```

## Docker

[Docker](https://hub.docker.com/r/kastang/ripme) for deploying an environment suitable to run RipMe by [@JoshKastang](https://github.com/JoshKastang) ([#469](https://github.com/4pr0n/ripme/issues/469))
