## [Link](http://www.joelonsoftware.com/articles/Unicode.html)
## Notes

### Historical Perspective
 - [ASCII](http://www.robelle.com/library/smugbook/ascii.html) was a standard that standardized English characters into numbers 32-127
    - This conveniently fit into 7 bits (which meant even in the older days of the 8 bit byte computers, you had a whole extra bit to potentially play around with)
    - problem with this was that everyone tried to do something different with these extra bit combinations. these different combinations bubbled up to what we call the ANSI standard now
 - Things were even more complicated for Asian countries with alphabets that would never fit into 8 bits and they tried to have some characters stored in 1 byte and others in 2. This created a funny side effect of making it simple to iterate through a string forward, but really hard to go backwards
 - Then [Unicode ](https://home.unicode.org/basic-info/overview/) comes along
    - A letter does not map to a specific set of bits, but instead something called a "code point" -- since letters are actually entirely symbolic, code points just map them to magic numbers established by the Unicode consortium that looks something like U+0041
 	   - U+ = "Unicode"
 	   - Numbers = hexadecimal representation of some unique character
 - With that concept, came the next challenge of figuring out how to encode these unicode letters into memory -- e.g. different platforms had different little/big endian things to worry about -- so this wasn't trivial
    - There was some weird [byte order mark](https://en.wikipedia.org/wiki/Byte_order_mark) used to identify the ends of each character, but I'm skipping over that for now
 - Then came the now-well-known [UTF-8](https://www.utf8.com/) standard
    - It effectively rolled up Unicode characters (all represented in hexadecimal magic numbers) to a variable number of bytes (octets)
    - So UTF-8 English (which could already fit into one byte) were more or less the same as the og ASCII characters (except it uses the theoretical concept of Unicode to actually represent things on the internet)
 - **Big takeaway**: there's no such thing as "plain text". It does not make sense to have a string without knowing its encoding
