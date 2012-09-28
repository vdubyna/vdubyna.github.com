---
layout: blog_entry
title: "Magento: Errors and exseptions"
---

Magento: Errors and exseptions.
===================================

This is rather dificult for developers who are not familiar with magento ecosystem
to find out wht is going on.
There are some tecniques what to do in such cases. Where to go and what to do.

Turn on Errors and Exceptions
-----------------------------

Open *index.php*.

* Find and uncomment `#ini_set('display_errors', 1);`
* Insert below this line `Mage::setIsDeveloperMode(true);`

The idea is to turn on *Developer Mode*.

All errors and exceptions are stored in *var/reports* (files with number of error)
and *var/log* (files *system.log* and *exception.log*)

Remember that sometimes Magento hide true error messages and show you only short notifies that there is an error.

Logs
----

To write something into log file

* `Mage::log('Message');` - will write a Message into *system.log* file by default
* `Mage::log(print_r($arrayOrObject, 1));` - will write an Array or object as a string into *system.log* file
(be carefull with big ones)
* `Mage::log('Message', null, 'mylog.log');` - will write a Message into *mylog.log* file
* `Mage::logException($exception);` - will process $exception object and write into exception.log file


Actions logs
------------

Magento Enterprise has `Enterprise_Logging` a [module](http://www.magentocommerce.com/knowledge-base/entry/configuration-advanced-admin-admin-actions-logging)
which stores the info about activities in the system.
Example: who, when and what changed. It is very useful to find out what was changed and what causes the problem.