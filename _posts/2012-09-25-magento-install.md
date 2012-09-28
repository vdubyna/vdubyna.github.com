---
layout: blog_entry
title: "Magento: install with Phing tool"
---

Magento: install with Phing tool
===========================================
Every day I have to do lot of experiments with modules, own code, configurations etc. And it is very useful to be able to restore clean Magento copy as fast as possible.
The Phing is a a greate tool which helps to do that.

Prepare
-------

First of all you have to install [Phing](http://www.phing.info/).
There is no problems with installation process if you pear is configured and ready to use.

	$ pear channel-discover pear.phing.info
	$ pear install phing/phing

Then just run it in the console

	$ phing -h

Next step is to load magento code into the working directory. I'm loading the last stable version from magento svn repository. Magento 2 is located in github.

	$ svn checkout http://svn.magentocommerce.com/source/branches/1.7

or

	$ git clone https://github.com/magento/magento2.git

To make you work even easier, there is integration with [PhpStorm](http://www.jetbrains.com/phpstorm/). There is a phing plugin. It will appear when you click in the sidebar on the *build.xml* and choose
`Add as Phing build file`

While first run it will ask you to input a directory to phing runner. To find it is easy with the help
of the command `$ which phing`


Configuration
-------------
Then let's create a dev space for our cool tools. Create a directory *dev* in magento root folder. Also add priveleges
to directories.

	$ chmod -R 777 var skin media
	$ mkdir dev
	$ cd dev

Now create 2 files *build.xml* and *build.properties*.
And put the content below into them.

<script src="https://gist.github.com/3775754.js"> </script>

It could be a greate tool if you add some more useful tasks. Example: clear cache, reindex all etc.

Usage
-----
In PhpStorm you can use plugin to run targets (tasks).
As for the console `phing -l` to see a list of targets and `phing mytarget` to run it.

    $ phing install

If you have got an error `sh: mysql: command not found` then replace `executable="mysql"` with a correct one for your
system. Ex: `executable="/usr/local/bin/mysql"`

