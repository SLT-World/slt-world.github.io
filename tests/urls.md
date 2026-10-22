---
layout: page
title: URLs
description: A collection of URLs used to evaluate browser functionality and behaviour.
permalink: /tests/urls.html
---

## Tricky URLs
### Simple
> - [Baseline case (example.test) (https)](https://example.test)
> - [Baseline case (example.test) (http)](http://example.test)
> - [Evil.test, for testing paths do not cause the evil.test origin to be hidden](https://evil.test)
> - [URL with username and password](https://user:pass@example.test)
> - [URL with non-default port](https://example.test:8080)
> - [URL with IPv4 literal hostname](http://127.0.0.1)
> - [URL with IPv6 literal hostname](http://[::1])
> - [data: URL](data:,Hello) (copy and paste URL in Chrome, which disallows top-level navigation to data: URLs)
> - [ftp:// URL](ftp://example.test)

### IDNs & Homoglyphs
#### RTL
> - [RTL url with LTR tld (https)](https://مثال.com)
> - [RTL url with RTL tld (https)](https://مثال.إختبار)
> - [LTR url with RTL tld (https)](https://example.إختبار)
> - [RTL url with LTR tld (http)](http://مثال.com)
> - [RTL url with RTL tld (http)](http://مثال.إختبار)
> - [LTR url with RTL tld (http)](http://example.إختبار)

#### Homoglyphs
> - [URL uses Cyrillic е instead of e](https://еxample.test)
> - [URL uses Cyrillic ӑ instead of a](https://еxӑmple.test)
> - [URL uses Cyrillic а in its own label](https://а.example.test)
> - [URL uses Cyrillic ӑ in its own label](https://ӑ.example.test)
> - [URL uses number one instead of l](https://examp1e.test)
> - [URL uses "vv" instead of "w"](https://vvikipedia.com)
> - [URL uses "0" instead of "o"](https://go0gle.com)
> - [URL with a single letter and numbers uses "O" instead of "0"](https://aO12.com)
> - [URL with a single letter and numbers uses "l" instead of "1"](https://a0l2.com)
> - [URL with a single letter and numbers uses Cyrillic а instead of Latin a](https://а012.com)
> - [URL with a single letter and numbers uses Greek α instead of Latin a](https://α012.com)
> - [URL with entire domain name "аррӏе" as all Cyrillic characters](https://аррӏе.com)

### Unusual characters
> - <a href="https://example.test/space-path-test ">URL with non-breaking space in path (U+202F)</a>
> - <a href="https://example.test/?space-path-test= ">URL with non-breaking space in query (U+202F)</a>
> - <a href="https://example.test/#space-path-test ">URL with non-breaking space in fragment (U+202F)</a>
> - [URL with a lock emoji in the domain](https://xn--https-5w14d.com)
> - [URL with a banana emoji in the domain](https://xn--banana-ox34e.com)
> - [URL with an emoji in its own label](https://🍌.example.com)
> - [URL with an emoji in its TLD](https://banana.🍌)
> - [URL with a lock emoji in the path](https://example.com/🔒)
> - [URL with a banana emoji in the query](https://example.com/?foo=🍌)
> - [URL with a banana emoji in the fragment](https://example.com/foo#🍌)
> - <a href="https://example.com/foo   bar">URL with spaces in the path</a>
> - <a href="https://example.com/?foo=   bar">URL with spaces in the query</a>
> - <a href="https://example.com/#foo   bar">URL with spaces in the fragment</a>

### Long
> - [Extremely long URL to trigger elision, ending in an url that looks similar to example.test](https://extremelylongurlmeanttotriggerelisionendinginadifferenturlextremelylongurlmeanttotriggerelisionendinginadifferenturlextremelylongurlmeanttotriggerelisionendinginadifferenturlexample.test)
> - [Extremely long URL to trigger elision, starting with a url that looks similar to example.test](https://example.test----extremelylongurlmeanttotriggerelisionendinginadifferenturlextremelylongurlmeanttotriggerelisionendinginadifferenturlextremelylongurlmeanttotriggerelisionendinginadifferenturl.test)
> - [A very long path ending in example.test](verylongpathverylongpathverylongpathverylongpathverylongpathverylongpathexample.test)
> - [A very long query ending in example.test](?verylongpathverylongpathverylongpathverylongpathverylongpathverylongpathexample.test)
> - [A very long fragment ending in example.test](#verylongpathverylongpathverylongpathverylongpathverylongpathverylongpathexample.test)
> - [URL with many subdomains](https://example.example.example.example.example.example.example.example.example.example.example.test)

### Short
> - [Very short URL](https://a.com)
> - [Very short URL that uses a Cyrillic a](https://а.com)
> - [Very short URL that uses a number](https://1.com)
> - [Very short URL that uses an underscore](https://_.com)

## Miscellaneous
### Accept: `text/markdown`
> - [Cloudflare](https://developers.cloudflare.com/)
> - [Bun](https://bun.sh/docs/runtime/file-types)
> - [Apidog](https://docs.apidog.com/)
> - [Mintlify](https://www.mintlify.com/docs/quickstart)
> - [Skeptrune](https://www.skeptrune.com/posts/use-the-accept-header-to-serve-markdown-instead-of-html-to-llms/)

### 404
> - [The White House](https://www.whitehouse.gov/energy/climate-change)
> - [Raspberry Pi Foundation](https://www.raspberrypi.org/piphone-home-made-raspberry-pi-smartphone/)

### PDF
> - [Sample PDF](https://ontheline.trincoll.edu/images/bookdown/sample-local-pdf.pdf)
> - [PDF Tables](https://assets.accessible-digital-documents.com/uploads/2017/01/sample-tables.pdf)

### SVG
> - [SVG Files](https://dev.w3.org/SVG/tools/svgweb/samples/svg-files/)

### Email
> - [reportapp@microsoft.com](reportapp@microsoft.com)