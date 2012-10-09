---
layout: blog_aentry
title: "MagentoEE: Exclude block from FPC"
active: false
---

When you write a custom block with a dynamic content and display it on
CLP (category landing page), PDP (product detail page) or CMS page - it will be cached for sure.

Solution
--------

We have to write own placeholder to teach Magento `PageCache` module not to touch our code and process it in a common way.


