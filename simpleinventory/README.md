# Simple Inventory

## Overview

This plugin is an EXTREMELY simple inventory. Its primary purpose is to track ownership of items.

The ownership of items **does not have any additional coded functionality** such as integrating weapons and armor with FS3, allowing customization of names or descriptions, crafting, or other functionality. It is purely informational.

The plugin contains the following features:

* The 'creation' of items in the system via configuration file. Items can have a name, a description, and a cost.
* The option to set items 'buyable' using luck.
* Characters with the manage_items permission can add and remove items from characters.
* An 'items' command that shows the items a character has.
* Equipping and unequipping items (one at a time)
* The ability to give items you own to other characters.

I have no plans to create a more complicated version of this or add any functionality, but you are welcome to fork the code and make your own changes as long as you credit Tat @ AresCentral.

## Installation

In the game, run `plugin/install <URL>`.

### Web Portal

Web Portal integration is optional. This will add a tab to the 'System' section of the character page which will list a character's items.

In aresmush/plugins/profile/custom_char_fields.rb, in `def self.get_fields_for_viewing` add:

> items: Simpleinventory.get_items(char)

In /app/templates/components/profile_custom_tabs.hbs, add:

>{{#if char.custom.items}}
>   \<li><a data-toggle="tab" href="#systemitems">Items\</a>\</li>
>{{/if}}

In /app/templates/components/profile_custom.hbs, add:

> {{#if char.custom.items}}
>\<div id="systemitems" class="tab-pane fade">
>  \<CharItems @char={{char}} />
>\</div>
>{{/if}}

## Configuration
In simple_inventory.yml:

`item_category:` The job category item/buy jobs posts to.

### Creating Items
In items.yml:

Items are built via configuration options. The item's name is the primary value, and it MUST be in Ruby titlecase. IE: `Sword Of Awesome` instead of `Sword of Awesome`.

`name:` 	Item name. This is display only and does NOT need to be in ruby-version titlecase.

`desc:`		Item description. It's a good idea to enclose these in double quotes "Desc" to prevent any weirdness with the use of apostrophes in descriptions. Line breaks can be created with \n

`available:` 	true/false 	- Is the item available for automatic purchase via item/buy?

`cost:` 	 	How many Luck Points does the item cost?






## Credits
Tat @ Ares Central
