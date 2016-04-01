## First steps

It's very simple to get started with Liquid.  A Liquid template is rendered in
two steps: Parse and Render.  For an overview of the Liquid syntax, please read
[[Liquid for Designers]].

```ruby
@template = Liquid::Template.parse("hi {{name}}")  # Parses and compiles the template
@template.render( 'name' => 'tobi' )               # Renders the output => "hi tobi"
```

The `parse` step creates a fully compiled template which can be re-used as often
as you like.  You can store it in memory or in a cache for faster rendering
later.

All parameters you want Liquid to work with have to be passed as parameters to
the `render` method.  Liquid does not know about your Ruby local, instance, and
global variables.

## Extending Liquid

Extending Liquid is very easy.  However, keep in mind that Liquid is a young
library and requires some outside help.  If you create useful filters and tags,
please consider making a [pull request](https://github.com/Shopify/liquid/pulls)
with them.

### Create your own filters

Filters are methods which take one or more
parameters and return a value. (For details on how to call a filter with multiple parameters, see the "Output" section of [Liquid for Designers](./Liquid-for-Designers).) You can use your own filters by:

1. Writing filter methods in a Ruby module. (A given module can contain any number of filter methods.)
2. Either passing an array of filter-containing modules to the render call (like `@template.render(assigns,
[MyTextFilters, MyDateFilters])`) or globally registering your filter modules (like `Liquid::Template.register_filter(TextFilter)`). 

With filters, note that Liquid just uses the method name as the filter name; there's no extra level of name-mapping like there is with tags and blocks. As such, make sure your filter method names don't conflict with any existing filters. 

```ruby
module TextFilter
  def textilize(input) # will be available as the "textilize" filter
    RedCloth.new(input).to_html
  end
end
```

```ruby
@template = Liquid::Template.parse(" {{ '*hi*' | textilize }} ")
@template.render({}, :filters => [TextFilter])              # => "<strong>hi</strong>"
```

Alternatively, you can register your filters globally:

```ruby
module TextFilter
  def textilize(input)
    RedCloth.new(input).to_html
  end
end

Liquid::Template.register_filter(TextFilter)
```

Once the filter is globally registered, you can simply use it:

```ruby
@template = Liquid::Template.parse(" {{ '*hi*' | textilize }} ")
@template.render              # => "<b>hi</b>"
```

### Create your own tags

"Tags" are tags that take any number of arguments, but do not contain a block of template code. 

To create a new tag, simply inherit from `Liquid::Tag` and register your class
with `Liquid::Template.register_tag`. The `register_tag` method takes two arguments: the user-facing name of the tag, and the class that implements it.

#### Arguments and initialization

Your tag class's `initialize` method must accept three arguments, and must call `super` at some point. 

* The first argument is the name of the tag. This is whatever gets passed to `Liquid::Template.register_tag` when the tag is registered. Usually you already know what your own tag's name is, but you can take advantage of this argument to avoid hardcoding things and repeating yourself (e.g. to ensure your error messages are consistent, etc.). 
* The second argument is whatever arguments were passed to your tag, as a single string. 
    * **Note** that Liquid provides no standard argument handling for custom tags (or even for its own built-in tags) — all you get is unstructured text, so you're in charge of determining how many arguments you got and validating their values. 
    * Liquid also provides no standard way to indicate whether an argument is meant to be an expression or a literal value, and it won't replace expressions with their value before passing them into your tag. Thus, if you need to treat an argument as an expression, you'll have to do something hairy like test it against the `Liquid::VariableSignature` constant and then call `Liquid::Variable.new(<ARGUMENT>).render(context)` somewhere in your own `render` method. 
* The third argument is a hash that stores Liquid options. By default it has two keys: `:locale` and `:line_numbers`, the first is a `Liquid::I18n` object, and the second, a boolean parameter that determines if error messages should display the line number the error occurred. This argument is used mostly to display localized error messages on Liquid built-in Tags and Filters.

#### Rendering

Your class must define a `render` method that takes one argument (`context`) and returns a string. The contents of the `context` argument will vary depending on the environment your tag is being used in.

If the output of your tag depends on the arguments it was called with in the template, you'll need to preserve those arguments as instance variables in your `initialize` method so they'll be available in `render`.

#### Example

```ruby
class Random < Liquid::Tag
  def initialize(tag_name, max, tokens)
     super
     @max = max.to_i
  end

  def render(context)
    rand(@max).to_s
  end
end

Liquid::Template.register_tag('random', Random)
```

```ruby
@template = Liquid::Template.parse(" {% random 5 %}")
@template.render    # => "3"
```

### Create your own tag blocks

"Blocks" are tags that contain a block of template code which is delimited by a `{% end<TAGNAME> %}` tag. The opening tag of a block can also take any number of arguments.

All tag blocks are parsed by Liquid.  To create a new block, you just have to
inherit from `Liquid::Block` and register your class with `Liquid::Template.register_tag`. The `register_tag` method takes two arguments: the user-facing name of the tag, and the class that implements it.

```ruby
class Random < Liquid::Block
  def initialize(tag_name, markup, tokens)
     super
     @rand = markup.to_i
  end

  def render(context)
    value = rand(@rand)
    super.sub('^^^', value.to_s)  # calling `super` returns the content of the block
  end
end

Liquid::Template.register_tag('random', Random)
```

```ruby
text = " {% random 5 %} you have drawn number ^^^, lucky you! {% endrandom %} "
@template = Liquid::Template.parse(text)
@template.render  # will return "you have drawn number 1, lucky you!" in 20% of cases
```

## Caching of classes

If you get errors like `A copy of ... has been removed from the module tree but is still active!` it's probably because Liquid is caching your classes in development mode, the solution is to disable it in test and development modes:

```ruby
# in config/environments/development.rb and config/environments/test.rb
Liquid.cache_classes = false
```