WWWU Game Design Club website
=============================

A crash course in jekyll
------------------------

### Installing

Follow the guides here: https://jekyllrb.com/docs/installation/

#### Windows

Installing jekyll on Windows is considerably more painful than the other Operating Systems, though there is a neat guide here: http://jekyll-windows.juthilo.com/ 

#### OSx

Make sure you have installed all the requirements. Python isn't necessary because we use Jekyll 3.x. 

One thing the documentation on the Jekyll website doesn't mention is the use of
the terminal. Once you have installed the requirements you should be able to
just type `gem install jekyll` into the terminal. Make sure you have the
development headers. If you don't then you'll get an error such as: `ERROR: Failed to build gem native extension.`

- In ubuntu: `sudo apt-get install ruby-dev` 
- I'm not too familiar with OSX, you'll have to do some research. [Here is what I found](http://stackoverflow.com/questions/761521/when-i-try-sudo-gem-install-json-i-get-the-following-error) 
### What Jekyll does

Jekyll is a static website generator. Basically it takes a lot of files and generates it into a website. 

### General Layout

The directory structure is set up as such:

#### The Root Directory (/)

In here, any `.md` or `.html` files will be generated as html files into the `_site` directory (more on that later). Generally, you're going to put your `index` here and all the other html pages. 

#### css

All the stylesheets go in here.

#### images

Self explanatory. Any images go in here.

#### _layouts

The point of jekyll is to make it easier to modify and edit html pages and to ensure that all redundant content is only edited in one place. `_layouts` is one way that jekyll does this. In here we put in the base layout for generic pages. Take a look at `page.html`. In here you'll notice it says `layout: default` surrounded by 3 dashes on the top and bottom. Keep that in mind and then open up `default.html` in the same `_layouts` directory. Look for the part where it says `{{ content }}`. What this keyword does is tell anything that has `layout: default` in their "frontmatter" (the thing surrounded by the three dashes on the top and bottom) to use this as the template. Anything that uses `layout: default` will be stuffed into the `{{ content }}` section of `default.html`. 

Something more mysterious is the `{% include head.html %}` and similar tags in the `default.html`. Which we'll cover now.

#### _includes

The includes directory is for content that will be included into every page. Think CSS imports, footers, headers, and their media. 

##### head.html

This file is for the any bit of HTML that should be included in the head. If you take a look at `default.html` in the `_layouts` directory again you should see that it includes this in the area where you would see the head included in a regular HTML file. However, if you change something in this single file, then it will be generated for all pages since every page inherits from `default.html`

##### header.html

This file is for the navigation.

##### footer.html

Finally, the footer is obviously just a file for the footer. 

#### _posts

Jekyll has support for blogging if we ever need a stream of posts (say news about future game jams or upcoming events) this would be the place to put them. Jekyll has a naming convention for each post though and it strictly follows it. You have to put the year, month, then day, then the post title. Like this: `2015-9-7-post-title.md`.

A template will need to be created in order to generate a page that shows all the files in `_posts`. This is out of scope for this document. 

Finally, posts are written in markdown. It's a simpler way to write content heavy text. Link here: https://daringfireball.net/projects/markdown/

#### _site

`_site` is where Jekyll puts the generated website from all your files. Do not track this folder with git! 

### _config.yml

This file is very important. Right now it doesn't do much but this stuff:

- Set the title of the website
- Set up a baseurl (important for when we migrate away from account!)
- Other variables.

Something useful that we can do with this file is set variables that we can access from our pages. Let's say we have multiple places where we display where we meet. Instead of just writing it out we could use a variable that we define in the `_config.yml`. We could define the room number in the config like this `room: CF 115`. We can then access this variable from any page by writing `{{ site.room }}`. 

### Prose.io

[prose.io](prose.io) is a website designed for managing websites through github pages. If we setup our website correctly then future clubs can use this tool to edit and make posts on our website without touching the HTML or installing jekyll. 

### Final Thoughts

Even if future club members decide to migrate away from using this system, it wont be hard for them to take our CSS from this repository and grab the generated HTML. This should make it make it (hopefully) easy to migrate to another system. 
