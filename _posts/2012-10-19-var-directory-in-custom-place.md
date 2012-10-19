---
layout: blog_entry
title: "Magento: Var directory in custom place"
---

Magento: Var directory in custom place
===============================

If you need to store cache sessions and the rest what is in var directory for the definite store in another place,
there is an easy possibility to do that.

All you need is to define `var_dir` as an option in `index.php` like this:

    Mage::run($mageRunCode, $mageRunType, array('var_dir' => BP . '/myvardirectory'));





