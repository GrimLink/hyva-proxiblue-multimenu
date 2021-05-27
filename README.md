# Hyva Compatible Multi Depth Menu based on category structure


## Introduction

The default Hyva menu if a flat 1 level category menu. I needed a multiple depth menu for a site build.
This is the end result.

## Install

You can install via composer:

* run: ```composer config repositories.github.repo.repman.io composer https://github.repo.repman.io```
* use composer ```composer require proxi-blue/multi-menu```
* enable: ```./bin/magento module:enable ProxiBlue_MultiMenu```
* run: ```./bin/magento setup:upgrade```
* run: ```./bin/magento setup:di:compile```


## Configuration

In admin, 

* Stores->Configuration->General->MultiMenu you can set the Category Depth.

This will determine how many levels of pullouts are displayed

* Stores->Configuration->General->Category Images you can set if teh category image should be set as an icon to the right

## Adding additional menu items (that is not categories)

You may want to add top level menu items, like example 'Contact Us'
You can add this by layout xml update in your theme ```default.xml``` layout file. Reference the block name ```topmenu_multimenu_additional```

```
<referenceBlock name="topmenu_multimenu_additional">
   <block name="topmenu_multimenu_additional_contactus" as="topmenu.additional.contactus"
       template="Magento_Theme::html/header/topmenu/additional/contact.phtml" ttl="3600"/>
</referenceBlock>
```

In the above example the contact.phtml file is as such:

```
<?php

use Magento\Framework\View\Element\Template;

/** @var Template $block */
?>

<button
    class="hidden 2xl:flex hover:bg-secondary-darker uppercase border-none bg-transparent
    outline-none focus:outline-none border py-1 rounded-sm flex items-center min-w-32">
        <span class="pr-1 font-normal flex-1">
                <a href="<?= $block->getUrl('contact-us') ?>"
                   title="Contact us"
                   class="block w-full whitespace-nowrap first:mt-0">
            Contact
                </a>
        </span>
</button>
```

## Usage

Well, it's a hover dropdown menu. Simply hover over memnu items, and the child items will be shown. 

![image](https://user-images.githubusercontent.com/4994260/119622514-ce63ea80-be39-11eb-87e6-be8f6efb2455.png)

To note is that the menu will detect the screen width end, and if any slide out items will breach the screen edge, they will be pulled to the left.

![image](https://user-images.githubusercontent.com/4994260/119622849-24d12900-be3a-11eb-8c28-5b2971edf50f.png)

Mobile view with Category Icons enabled

![image](https://user-images.githubusercontent.com/4994260/119846015-57634a80-bf3c-11eb-809b-42bf56f8395d.png)

## Notes

I am not a master and frontend. Much can likely be improved.

This is not pure alpineJS. There is a portion of vanilla JS involved. SOme can likely be refactored to be more pure Alpine, 
but I am still learning and don't know all the moving parts for alpine, as yet.
As my knowledge progress I plan to refactor parts.

Feel free to contribute with PR's, as I can also learn from this, from you.

I needed this working for a client build, so it is AS IS.

## Credits

The original tailwind css based menu dropdown was based on https://tailwindcomponents.com/component/nestable-dropdown-menu
