# A list of all of ripmes config options and what they do
### To change these option on your ripme install edit the rip.properties file

The config file is at

%LOCALAPPDATA%\ripme on Windows

$HOME/.config/ripme on *Nix

$HOME/Library/Application Support/ripme on MacOS

### file.overwrite

bool

If true ripme will overwrite existing files rather than skip them

### clipboard.autorip

bool

If true ripme will try to download any links in the clip board

### error.skip404

bool

Don't retry on 404 errors

### download.save_order

bool

If true ripme will prefix each downloaded file with a number in the order the file was download

### auto.update

bool

If true ripme will auto-update every time it's started

### tumblr.get_raw_image

bool

If true the tumblr ripper will download the image in the size it was uploaded in

### play.sound

bool

If true ripme will play a sound every time a rip finishes

### download.show_popup

bool

TODO figure out what this is for

### log.save

bool

If true ripme will save it's logs

### urls_only.save

bool

If true ripme will save all urls to a text file and download no files

### album_titles.save

bool

Currently does nothing

### prefer.mp4

bool

Prefer mp4 when downloading a video that has more than 1 format

### history.warn_before_delete

bool

If true ripme will prompt the user with a "Are you sure?" box when clearing ripmes download history

### instagram.download_images_only

bool

If true the instagram ripper will skip videos and only download images

### download.timeout

int

File download timeout (in milliseconds)

### page.timeout

int

Page download timeout (in milliseconds)

### download.max_size

int

Maximum size of downloaded files in bytes

### threads.size

int

The number of threads to use

### twitter.max_requests

int

TODO figure out what this is for

### history.end_rip_after_already_seen

int

The max number of times download a url will fail with "Already downloaded" before the rip stops.

### twitter.auth

String

Twitter API key (Base64'd)

### tumblr.auth

String

Tumblr API key

### log.level

String

The debug log level (Example: Log level: Debug)

### gw.api

String

TODO figure out what this is for

### 8muses.use_short_names

Bool

If true ripme saves images from 8muses with only the page number as the filename

### proxy.http

String

HTTP Proxy (format [user:password]@host[:port]) WARNING: see https://stackoverflow.com/q/41505219 for HTTP Proxy with user/password

### proxy.socks

String

SOCKS Proxy (format [user:password]@host[:port])

### lang

String

What language to use for ripmes UI

Example to display the UI in German set lang to "de_DE"

### nhentai.blacklist.tags

String

A comma separated list of tags which if present on a nhentai album will cause ripme to skip it

Example: Adding "nhentai.blacklist.tags = one,two, three" will cause ripme to skip any nhentai album with the tags one, two or three

### ehentai.blacklist.tags

String

A comma separated list of tags which if present on a ehentai album will cause ripme to skip it

Example: Adding "nhentai.blacklist.tags = one,two, three" will cause ripme to skip any ehentai album with the tags one, two or three

### e621.cookies

String

A list of e621 cookies. Used for login (to disable global blacklist) or to bypass Cloudflare captcha protection (in combination with e621.useragent). See https://github.com/RipMeApp/ripme/issues/1604#issuecomment-611507949

Example (login cookie): e621.cookies = remember=DfhEx27X0Ok5Y8T3D9NEvqqsEJKJ7Wp7ZYZT6Gp4W8cXMrmtnZRiyrvRDlNBqiWonHzaJccjAOVJq2F6DBNJZ8%2FmRwmo9neNPPUqKODHJ%2BE8N1UQvL0Fuued1gDjJX0ec
Example (captcha bypass): e621.cookies = \_\_cfduid=d223ffab289db674e672307328be56a23f72;cf_clearance=ab76532094bc24424935dab1232b36420-9273251468ba524ec

### e621.useragent

String

Used to bypass Cloudlare captcha.

Useragent string of the browser you used to complete the captcha.

Example: e621.useragent =  Mozilla/5.0 (X11; Linux x86_64; rv:74.0) Gecko/20100101 Firefox/74.0 