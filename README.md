# Sublimetheme


## Description

Sublimetheme is a Ruby package that allows you to easily create a Sublime text Color Scheme with with as little as six lines of code.

## Requirements
* Any version of Ruby

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'sublimetheme'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install sublimetheme

  >or otherwise download the [gem file](https://rubygems.org/gems/sublimetheme)


## Module name

### Sublimetheme

Contains a class **Make** that takes two arguments ``(Theme name)`` and ``(Author's name)`` and 162 other methods that takes no arguments. one of them is **scopes()** that prints out all the supported 161 programming languages available and their `syntax highlight scopes`. For example to print all the *syntax highlight scopes* for C++, just call `.cpp()` on your module. i.e. ``Sublimetheme.cpp()``

#### Make

**Make** has six methods which are:

* start() --> This creates the xml header.
* head() --> This creates the basic and most requireant features of your theme. e.g. foreground, background, caret, invisibles, line highlight, selection, find highlight, find highlight foreground, selection border and stack guide color. These are optional parameters too.
* body() --> This is completely optional and is the main area for your color scheme customization. You can add as many body methods as possible. ``If none is given, you will have a slighly customized theme similar to Python's IDLE theme``.
* complete() --> This completes the theme.
* readme() --> Although completely optional, it makes a README.md file and this is useful if you want to publish it.
* package() --> Although completely optional, it creates a packages.json file which is useful if you want to share your theme on the [Package control website](https://packagecontrol.io)


>Before you can use the Make class, you need to require the Sublimetheme module the following way

##### Method arguments

**start()** takes no arguments
**head()** between **0** to **10** arguments *(just like hashes)* then supply a *HEX color value* to the hash symbol.

```ruby

> options are:
	ag --> activeGuide
	bg --> background
	ct --> caret
	fg --> foreground
	fh --> findHighlight
	fhf --> findHighlightForeground
	gf --> gutterForeground
	gu --> guide
	gut --> gutter
	ins --> inactiveSelection
	inv --> invisibles
	lh --> lineHighlight
	sb --> selectionBorder
	se --> selection
	sg --> stackGuide

```
> See example below.

**body** takes **two arguments** being `(scope description)` and `(scope)` and optional kwargs arguments (hash) whick keys can be combined. they are fg, fs and bg. 

> (See head options)

**complete** takes an optional UUID (Universally Unique identifier) argument. Although not necesssary but you wouldn't want your `.tmTheme` file to have the same UUID with other people's `.tmTheme` file. You can get a free one via an  [UUID online generator tool](https://www.uuidgenerator.net)

**readme** takes three optional values (**repository or dedicated website URL**), (**user email**) and (**image name e.g. preview.png**)

> If you ignore the third image link, no image section would be generated in the readme section. Likewise if no URL and email argument is provided, its readme section will be blank.


**package** This takes a repository URL and fills it into `packages.json` file which can then be copied into the necessary repository folder of the package control repo in github.

##### Usage

```ruby

	require "sublimetheme"	

```

You can then use it by creating an instance of the Make class and calling the necessary methods.

```ruby

	sample = Sublimetheme::Make.new("Teddy", "Mr Bean")
	sample.start()
	sample.head(fg: "#000", bg: "#FFFFFF", ct: "#F00", inv: "#0FF", lh: "#004312", se: "#eeffee", fh: "#00BFFF", fhf: "f0f0f0", sb: "#E996F7", sg: "#abcdef")


	sample.body('Ruby: Numbers', 'constant.numeric.ruby', fs: 'italic', fg: '#f0f', bg: '#0ff')
	sample.body("C++ keyword", "keyword.control.c++", fs: "bold italic underline", fg: "#ff0000")


	sample.complete(uuid="c5873966-71ae-43da-8711-a22542e06922")
	sample.readme("github.com/mrbean/teddy", "mrbean@teddy.com", "teddy.jpg")
	sample.package("github.com/mrbean/teddy")

```

This will generate an IDLE-like color scheme with two extra syntax highlighting for Ruby numbers and C++ keywords.

> Make sure you follow the order of the called methods but you can add as many body elements as possible which must come before **.complete()** and after **.head()**



#### Scopes

The **Scopes** method when used along 161 other methods is helpful for showing several programming language scopes. It lists all the 161 supported programming languages and their syntax highlight scopes. You can also view all the scopes directly on [Github](https://github.com/tushortz/scopes). You can then call your desired programming language name to see all the syntax highlight scopes it supports.


> Before you can use the scope method, you need to require the Sublimetheme module the following way 

##### Usage

```ruby

	require "sublimetheme"	

```

You can then use it by calling the method like the below example

```ruby

	Sublimetheme.scopes()

```

This will print a result similar to this:

```ruby


	Scope Name: scope
	=================
	Actionscript: source.actionscript
	Active4D: source.active4d
	Active4D_Html: text.html.strict.active4d
	Active4D_Ini: text.active4d-ini
	Active4D_Library: source.active4d.library
	Ada: source.ada

	.... etc ......
```

If you already know the language you want to use but need it's syntax highlighing scope then all you need do is call the method directly e.g.

```ruby

	Sublimetheme.cpp()

```

will give a result similar to this:

```ruby

	C++ 
	===
	Scope name: source.c++

	C++
	entity.name.function.c
	keyword.control.c++
	keyword.operator.c++
	keyword.operator.cast.c++
	meta.function.constructor.c++
	meta.function.destructor.c++
	meta.function.destructor.prototype.c++

	..... etc ......
```






## Using locally

If you just want to use your **.tmTheme** locally, copy your generated `.tmTheme` into the sublime text packages 

	`Packages` --> `Color Scheme - Default`. 

You will then be able to use it by going to:

	`Preferences` --> `Color Scheme - Default` --> `Themename`


## Acknowledgements

I was inspired to write this package after creating my own Sublime text color scheme called [Wildlife](https://packagecontrol.io/packages/Wildlife). It was a really tedious and energy drenching job but thank God this is now available for anyone and makes things easier to use.

All glory belongs to God for helping me in completing this. Without him, this couldn't have been written by me.


## Contact

If further information or if help is needed, feel free to contact me on my email at taiwo.kareem36@gmail.com



<!-- ## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).
 -->
## Contributing

Bug reports and pull requests are welcome on [GitHub](https://github.com/tushortz/sublimetheme). This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://.contributor-covenant.org) code of conduct.


## License

The gem is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

**Copyright © 2015 Taiwo Kareem**