This guide explains how to rip from an unsupported website using RipMe.

If you like to learn by example, check out the simple [`ImgboxRipper.java`](https://github.com/4pr0n/ripme/blob/master/src/main/java/com/rarchives/ripme/ripper/rippers/ImgboxRipper.java).

### Expectations
* Some knowledge of `git`
* Some knowledge of the Java programming language
* Some knowledge of the HTML DOM, CSS selectors, and the like.

## Step 0: [Fork this repo](https://help.github.com/articles/fork-a-repo)

## Step 1: Create a new .java file
Create the file within [`/ src / main / java / com / rarchives / ripme / ripper / rippers`](https://github.com/4pr0n/ripme/tree/master/src/main/java/com/rarchives/ripme/ripper/rippers)

File should follow the naming scheme `<Site>Ripper.java`

## Step 2: Extend the [`AbstractHTMLRipper` class](https://github.com/4pr0n/ripme/blob/master/src/main/java/com/rarchives/ripme/ripper/AbstractHTMLRipper.java)

```java
public class YoursiteRipper extends AbstractHTMLRipper {
```

## Step 3: Understand the fields available

By extending `AbstractHTMLRipper`, you have access to the `this.url` object containing the URL to be ripped.

## Step 4: Override the required methods

The methods below are defined in `AbstractHTMLRipper` and should be overridden in your .java file.

---

```java
String getHost()
```
Returns: The **name** of the website (no need for `.com`).  
This String is used in naming the save directory.  
Example: `imgur`

---

```java
String getDomain()
```
Returns: The **domain** of the website.  
This String is used in the `canRip()` method to determine if a URL can be ripped.  
Example: `imgur.com`

---

```java
String getGID(URL)
```
Returns: A unique identifier for the album (*Gallery ID* or *GID*).

Note: The URL to every album on the website should return a **different** GID.  
*This is because the save directory will be named in the scheme `HOST_GID`*

Most rippers use `regex` to strip out the GID.

Example: `imgur.com/a/abc123` could return `abc123`  
Example: `somesite.com/gallery.php?id=4321` could return `4321`

---

```java
Document getFirstPage()
```

Returns: A Jsoup `Document` object containing the contents of the first page.  

Tip: Use the [`Http` class](https://github.com/4pr0n/ripme/blob/master/src/main/java/com/rarchives/ripme/utils/Http.java) for easy methods of retrieving the page.

**Most** rippers simply `return Http.url(this.url).get()`.  
This works for the majority of websites (most sites don't require cookies, referrers, etc).

```java
Document getNextPage(Document) // Optional!
```
Input: Jsoup `Document` retrieved in the `getFirstPage()` method.  
Returns: The *next* page to retrieve.  
Throws: `IOException` if no next page can be retrieved.

By default, this method throws an `IOException` within `AbstractHTMLRipper`, meaning it assumes there is no **next page**. Override this method & retrieve the next page if you need to rip multiple pages. See [`ImagebamRipper.java`](https://github.com/4pr0n/ripme/blob/master/src/main/java/com/rarchives/ripme/ripper/rippers/ImagebamRipper.java#L70) for an example of how this is used.

```java
List<String> getURLsFromPage(Document)
```
Input: Jsoup `Document` retrieved in the `getFirstPage()` method (and optionally the `getNextPage()` method).  
Returns: List of URLs to be downloaded or retrieved.

This is where the URLs are *extracted* from the page Document.  
Some rippers return a list of subpages to be ripped in separate threads (e.g. [`ImagevenueRipper.java](https://github.com/4pr0n/ripme/blob/master/src/main/java/com/rarchives/ripme/ripper/rippers/ImagevenueRipper.java#L67)

This is when CSS-Selectors come in handy. Say you wanted to grab every image that appears on the page:

```java
List<String> result = new ArrayList<String>();
for (Element el : document.select("img")) {
  el.add(el.attr("src"));
}
return result
```

This would return the source to all images on the page (although they will likely be thumbnails).

The URLs returned are passed into the next method...

---

```java
void downloadURL(URL url, int index)
```

Input: `URL`: One of the URLs returned by `getURLsFromPage()`  
Input: `index`: The *number* for this URL (whether it's the 1st image, 2nd image, etc).

This is where your ripper *downloads* the image/file.  
Most rippers simply use the `AlbumRipper`'s method:
```java
@Override
public void downloadURL(URL url, int index) {
  addURLToDownload(url, getPrefix(index));
}
```

The above will download the URL to the appropriate save directory, guessing the filename to save based on the `url` and the `index`.
