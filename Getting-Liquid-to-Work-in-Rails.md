Liquid no longer comes with a rails template handler making the text below outdated, see this issue https://github.com/Shopify/liquid/issues/21

To start using liquid just extract it into vendor/plugins or better yet use the ./script/plugin script to install liquid.

You can now start using templates with the .liquid file type.

### Notes

A note about helpers. The liquid rails plugin tries to use your helpers as Filters. Your helpers will always receive the piped in text as first parameter and any Filter parameters after this.

Helper:

```ruby
module ApplicationHelper
  def truncate(input, length)
    input[0..length] + '...' 
  end
end
```

Liquid:

```liquid
{{ 'This is a long section of text' | truncate: 3 }} #=>   Thi... 
```