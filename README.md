Order Export
===========

Order export is a quick and dirty extension I wrote as an implementation for a client - basically, it exports line items to a CSV file.

I chose not to use spree-advanced-reporting after taking a look at how complex it was and running into a couple of problems getting it going. Plus, I was going to have to write a template to export the right data anyway.

You can install it simply by adding it to the Gemfile of your Spree project:
`gem 'order_export', :git => 'git://github.com:3months/spree-order-export.git'`
And then running `bundle install`

The extension adds a report under the 'Reports' tab which allows the export to be constrained to a date range, and exports a CSV file which should be in a blend of line breaks and seperaters which should work with Microsoft Office Excel.

It exports the following fields, in the following order:
* Order number
* Customer Full Name
* Customer Address (Address 1, Address 2 if there, Country)
* Customer Phone
* Customer Email
* Variant (Product) name
* Variant (Product) quantity
* Order total
* Order payment method.

I played around with dynamically adding (fastercsv)[http://fastercsv.rubyforge.org/] as a dependency in the Gemfile, but didn't have any luck - therefore, if you are running *Ruby 1.8.7* you need to add `fastercsv` to your Gemfile, otherwise you will run into an exception from my controller when I `require 'fastercsv'`. If you are using *Ruby 1.9.2* you'll be OK as FasterCSV is the new default CSV library in this version, but I have had to call methods on the `FasterCSV` module instead of `CSV` to be backwards compatible with 1.8.7

I simply implemented this feature as a Spree extension to help out someone else needing this sort of basic funcionality as part of work on a project, rather than specifically aiming to build it as a complete extension - therefore, I can vouch that it works for me, and should work for you, but *if you need to change anything about which fields are exported or how the extension works* there is no sort of configuration - fork the extension, and implement whatever you need to on your copy.

Enjoy :-)

_Josh_





Copyright (c) 2011 Josh McArthur, released under the MIT License

