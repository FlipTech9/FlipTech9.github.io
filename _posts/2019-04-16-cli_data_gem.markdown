---
layout: post
title:      "CLI Data Gem"
date:       2019-04-16 09:18:25 +0000
permalink:  cli_data_gem
---




This is my first blog post about my first CLI Application. I'll walk you through web scraping and how I used it for this project. I utilized open-uri (to save and open a webpage) and Nokogiri (to parse HTML / CSS selectors). 

I wanted to scrape Puma.com and list current sales of men's shoes. Creating a constant for URL will allow us to access product pages in another method.

`PUMA = "https://us.puma.com/en/us/mens/sale/shoes"`

Then we create a class method using "self." to scrape page:


```
def self.scrape_page

		html = open(PUMA)
		doc = Nokogiri::HTML(html)
```

Next we identify the CSS selectors from the nokogiri node sets to retrive the data we are looking for, iterate over the array, create variables, and save data:

```
doc.css("div.product-grid__container div.product-tile div.tile-body div.pdp-link").each do |product_name|
            
            name = product_name.css("a").text.strip
            url = product_name.css("a").attr("href").value
            product_name = PumaCli::Products.new(name, url)
            product_name.save
        end 
       
    end
		```
		
With this information we can create another class method with product details to display to the user.
		
		
		
A *Products* class is responsible for the storing the scraped data.  The class variable *@@all* stores data in an array and instance variables *@name* and *@url* are declared here. There are attribute accessors defined here as well however *:name* and *:url* are the only ones intialized. 


The *CLI* class provides the user interface in the terminal. The methods defined here start the application, list sales, provide menu prompts, and closes the program.

There's an environment file to associate required classess and gems:

```
require "nokogiri"
require "open-uri"
require "pry

#and any require_relative paths to defined classes

```

Finally in our executable file we instantiate a new instance of the method that runs the application. 

More information can be found in [repository.](https://github.com/FlipTech9/puma_cli)


