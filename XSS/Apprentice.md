# [Reflected XSS into HTML context with nothing encoded](https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded)

The search field has the `search` parameter, where it is reflected in the `h1` tag, which informs the number of results found and the text searched.

The failure occurs when rendering this text, as no verification of the characters sent is performed.

To fix this vulnerability, you need to escape special characters, such as the following: `'`, `"`, `<`, `>`

My solution: `<token>.web-security-academy.net/?search=aaa<script>alert(1)</script>`

