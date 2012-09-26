---
layout: blog_entry
title: "Magento: Tests - quick start"
---

Tests - quick start
===================
Very often we need to test our scripts. But we have not frontend.
It is not a secret that to cover your custom module in magento with `unit tests` is a really a complex work.
And it can be more complex then feature itself. But all the same we can write tests and save our nerves.

Tools
-----
> If you see this message that means that the article is in dev mode still. thus there could be errors.

* [PhpUnit](http://www.phpunit.de/manual/current/en/index.html)

Dev Space
---------
When I start to work on a new project, the first thing I do is creating a cosy and comfortable space where I can do something cool. As a practice shows, it helps to improve your skills as a developer and to receive a lot fun playing with code there.

I do it in a directory `/dev` in a `Document Root`.

First touch
-----------
First of all, configure your application to be ready to run tests at any time you want. I'm usinng this directory structure, but feel free to find a better one.

	/dev
	  |_ bootstrap.php
	  |_ phpunit.xml
	  |_ /tests
	  |_ /tests/MageTestCase.php

The code for them you can find there:


Usage
-----

If I need a test. Usualy I create a folder in the tests directory with a similar to the namecpace and module name.

Example:

	/dev/tests/Mycompany/Module/OpenPageTest.php

This is a very minimum to work.

And we are ready to run tests now.

	$ phpunit

This will run all tests in the directory


Break the borders
-----------------

I'm often use tests not only for testing but for running pieces of my code to see how that work. And PhpUnit with all its helpers of checking does a lot of asistance for me.



