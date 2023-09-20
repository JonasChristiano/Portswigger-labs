# [Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)

The search field has the `search` parameter, where it is reflected in the `h1` tag, which informs the number of results found and the text searched.

The failure occurs when rendering this text, as no verification of the characters sent is performed.

To fix this vulnerability, you need to escape special characters, such as the following: `'`, `"`, `<`, `>`

**Type:** Reflected

**My solution:** `<token>.web-security-academy.net/?search=aaa<script>alert(1)</script>`

# [Stored XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded)

When checking the functionality of commenting on a post, it was observed that the `comment` parameter, where is reflected in the `p` tag, which is where the comment is shown

The failure occurs when rendering this comment, as no verification of the characters sent is performed.

To fix this vulnerability, you need to escape special characters such as the following: `'`, `"`, `<`, `>`

**Type: Storage

**My Solution:** I needed to fill in the comment field with the following content: `It's a comment<script>alert(1)</script>`

# [DOM XSS in `document.write` sink using source `location.search`](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink)

Analyzing how the search field works, I noticed that it creates the `img` tag, and it receives a path that contains a parameter where it should open an image, but as there is no processing of user input in the function where this is created tag allowing the vulnerability.

The failure occurs when rendering this comment, as no verification of the characters sent is performed.

To fix this vulnerability, you need to escape special characters such as the following: `'`, `"`, `<`, `>`

**Type:** DOM-Base

**My Solution:** a"><script>alert(document.cookies)</script>

# [DOM XSS in `innerHTML` sink using source `location.search`](https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink)

Analyzing the operation of the search field, the search value is inserted in the `span` tag, as the inserted text is interpreted as HTML, the use of any tag is permitted, however the use of the `script` tag has no effect, as it is inserted after the page loads.

To solve this problem, two measures can be taken:
1st. Handle user input by encoding special characters
2º Do not use `innerHTML`, if it is necessary to use other means such as `innerText`. However, there are still risks of using this alternative, it is recommended to process the user input.

**Type:** DOM-Base

**My solution:** `<token>.web-security-academy.net/?search=<img+src+onerror%3Dalert%281%29>`
























