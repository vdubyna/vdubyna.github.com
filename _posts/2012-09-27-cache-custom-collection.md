---
layout: blog_entry
title: "Magento: Cache custom collection"
active: false
---

To speed up page loading the cache is the most powerful tool for this.


Zend Cache
----------

Magento uses [Zend Cache](http://framework.zend.com/manual/1.12/en/zend.cache.html) to manage it.

Save in cache
-------------

So to cache the collection you have to do the following:

* Define a unique id to store a content in cache
* Add an observer to Entity CRUD operations to cetch the events when you have to clean it

Clean cache
-----------





