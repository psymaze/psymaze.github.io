---
layout: post
title: Github Pages绑定域名

---

博客托管在Github，域名是在namesilo注册的。但是使用CNAME绑定apex domain时总时遇到问题。搜索到namesilo官网给出的[解释](https://www.namesilo.com/Support/DNS-Manager)：

> A common problem encountered with CNAME records when integrating with 3rd party site hosting services is that www.domain.com CNAME records are easily created, but creating the CNAME record for just domain.com (to capture traffic when people don't type in "www.") cannot be done since that goes against [RFC1034](http://tools.ietf.org/html/rfc1034). We have a work around for customers with this issue - our domain parking system redirects any "naked" domains (i.e. the SLD - domain.com) to the www.domain.com equivalent. Therefore, all that must be done is to create an A record to our parking IP (which can be done by applying the parking/forwarding DNS template) for the SLD hostname.

也查到一个GitHub官网给出的[建议](https://help.github.com/en/github/working-with-github-pages/about-custom-domains-and-github-pages)：

> `www` subdomains are the most stable type of custom domain because `www` subdomains are not affected by changes to the IP addresses of GitHub's servers. Your site will also load faster because Denial of Service (DoS) attack protection can be implemented more efficiently.

虽然GitHub更建议使用www subdomains，但是我从个人的感官来说，我更偏爱apex domain，所以还是绑定了[psymaze.com](https://psymaze.com/)。另外设置www.psymaze.com跳转到[psymaze.com](https://psymaze.com/)。