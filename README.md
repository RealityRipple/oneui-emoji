# Samsung OneUI Emoji Extractor
A JS script to extract Emojis in 112x112 pixel PNG format from SamsungColorEmoji.  

## Requirements
 - Building the image list with `index.html` requires a chromium-based web browser.
 - Due to CORS, the `emoji-test.txt` file is pulled from RealityRipple Software instead of unicode.org.
 - Before running the script, please change the following settings in your browser:
   - `Downloads`:
     - `Location`: should be the path you wish to save the PNG files, such as `./png/112`.
     - `Ask where to save each file before downloading`: **off** as there are nearly 4000 files to save.
     - `Show downloads when they're done`: **off** to reduce load delay.
   - `Privacy and security` -> `Permissions` -> `Additional permissions` -> `Automatic downloads`:
     - `Allowed to automatically download multiple files`: add a new site with the URL `file:///*`.

## Additional Notes
I was unable to find a Node package that could correctly parse SamsungColorEmoji, or load it into Node's `canvas` implementation. This drastically reduces the automatability of this project.

Due to an issue with the canvas element in chromium browsers, some emojis, particularly those with ZWJs from Unicode 15.1 onward occasionally fail to render correctly. The kludge to resolve this was to render the same emoji twice, with no space between, and then ignore the first of the two Emojis, as only the second one renders correctly.  

Acquiring the Samsung OneUI emoji font can be difficult - the current copy in use by this repository is from https://github.com/caffeinepyroxene/oneui-emojis - which is OneUI 7 from January of 2025.  

OneUI does not have the "eye in speech bubble" emoji, also known as the "I Am a Witness" or "see something, say something" icon, `1f441-fe0f-200d-1f5e8-fe0f`. It was last included in Samsung Experience 9, circa 2018. Oddly, the speech bubble emoji is still shaped like an eye, but the two emojis do not exactly overlap cleanly. I've made a simple mockup PNG of this emoji from the two existing OneUI emojis, which may be used in place of the missing glyph.