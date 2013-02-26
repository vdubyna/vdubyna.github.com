---
layout: blog_entry
title: "Magento: Manage cache of blocks"
---

Magento: Manage cache of blocks
===============================

Magento has good and flexible cache system on the level of blocks. It is based on
[Zend Cache](http://framework.zend.com/manual/1.12/ru/zend.cache.html). But by default all blocks are excluded from cache
even if they could be. How to tell magento cache my block and increase the spead of page loading.

Solution
--------

Let's deep into the code and look at this part

{% highlight php %}
<?php
// app/code/core/Mage/Core/Block/Abstract.php
protected function _saveCache($data)
{
    if (is_null($this->getCacheLifetime()) || !Mage::app()->useCache(self::CACHE_GROUP)) {
        return false;
    }
    $cacheKey = $this->getCacheKey();
    /** @var $session Mage_Core_Model_Session */
    $session = Mage::getSingleton('core/session');
    $data = str_replace(
        $session->getSessionIdQueryParam() . '=' . $session->getEncryptedSessionId(),
        $this->_getSidPlaceholder($cacheKey),
        $data
    );

    Mage::app()->saveCache($data, $cacheKey, $this->getCacheTags(), $this->getCacheLifetime());
    return $this;
}
{% endhighlight %}


There we can see that save cache works only if current block has the data `cache_lifetime`
otherwice it will not go further.

The easiest way to do that is to use a power of `xml` configuration.

{% highlight xml %}
<block name="myspace_fpcblock_time" type="Myspace_Mymodule_Block_Time" template="time.phtml">
    <action method="setAttribute"><name>cache_lifetime</name><value>8000</value></action>
</block>
{% endhighlight %}

Action `setAttribute` is a proxy to `setData` of Varien_Object class.






