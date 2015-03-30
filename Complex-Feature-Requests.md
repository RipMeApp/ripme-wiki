# Remember image URLs ([#163](https://github.com/4pr0n/ripme/issues/163))
* Remember every image ripped, save to file (or history?)
* Store URLs in history, use stored URLs to avoid duplicates
* Ability to clear URLs to re-rip all images

# Stop ripping already-ripped content ([#73](https://github.com/4pr0n/ripme/issues/73) [#76](https://github.com/4pr0n/ripme/issues/76))
* Basic idea: Re-ripping a site should stop when we hit content that we've already gotten, i.e. ripping a subreddit (sorte by new), tumblr page, etc.
* Could be a boolean in [AlbumRipper](https://github.com/4pr0n/ripme/blob/master/src/main/java/com/rarchives/ripme/ripper/AlbumRipper.java#L31-L34)
* Note: Need to watch out for reposts/false-duplicates (same URL but hasn't been ripped before)
 * Could be alleviated by storing the most-recent `timestamp` (reddit and tumblr expose the timestamp in their APIs).

# Subscriptions ([#162](https://github.com/4pr0n/ripme/issues/162), [#176](https://github.com/4pr0n/ripme/issues/176), [#190](https://github.com/4pr0n/ripme/issues/190))
* Re-rips the album every X minutes/hours.
* Could be another checkbox or "clock" icon in the History page.
 * Clicking the "clock" would show a prompt ("How often should this album be re-ripped?")
 * Or a `Subscribe` button below everything else.
 * Or a right-click popup menu to "Subscribe: X minutes" and "Unsubscribe"