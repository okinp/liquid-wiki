I've collected some 'drop classes' from Mephisto in the hope of understanding
how to stitch Liquid into a Rails App.

Perhaps someone can comment on what the different drops are doing and their
purpose.

Here are the 'drops'

```ruby
class UserDrop < BaseDrop
  liquid_attributes << :login << :email
end
```

### Explanation of above code

Liquid accepts only a limited number of objects types i.e. Strings, Arrays,
Hashes, Numerics, and Booleans. If we want to pass our Active Record object to
liquid templates we have to define that logic explicitly(Liquid doesn't provide
that functionality).  Basically there are three methods/ways to define that
logic.

[[Getting Liquid to Work in Rails]]

The above describe method will constructs a Liquid Drop with the methods you
included. After including the above said stuff you will be able to access user's
email and login in the liquid template ie {{ user.email }} and {{ user.login }}.
Only email and login will be available in the liquid template (all other methods
will not be accessible to liquid templates i.e. user.password ).

```ruby
class ArticleDrop < BaseDrop
  include Mephisto::Liquid::UrlMethods

  timezone_dates :published_at, :updated_at
  liquid_attributes << :title << :permalink << :comments_count

  def initialize(source, options = {})
    super source
    @options        = options
    @liquid.update \
      'body'             => @source.body_html,
      'excerpt'          => (@source.excerpt_html.nil? ||
                             @source.excerpt_html.empty? ? nil : @source.excerpt_html),
      'accept_comments'  => @source.accept_comments?,
      'is_page_home'     => (options[:page] == true)
  end

  def author
    @author ||= liquify(@source.user).first
  end

  def comments
    @comments ||= liquify(*@source.comments.reject(&:new_record?))
  end

  def sections
    @sections ||= @source.sections.inject([]) { |all, s|
      s.home? ? all : all << s.to_liquid } # your days are numbered, home section!
    @sections ||= liquify(*@source.sections) { |s| s.home? ? nil : s.to_liquid }
  end

  def tags
    @tags ||= liquify(*@source.tags)
  end

  def blog_sections
    sections.select { |s| s.source.blog? }
  end

  def page_sections
    sections.select { |s| s.source.paged? }
  end

  def content
    @content ||= body_for_mode(@options[:mode] || :list)
  end

  def url
    @url ||= absolute_url(@site.permalink_for(@source))
  end

  def comments_feed_url
    @comments_feed_url ||= url + '/comments.xml'
  end

  def changes_feed_url
    @changes_feed_url ||= url + '/changes.xml'
  end

  protected
    def body_for_mode(mode)
      contents = [before_method(:excerpt), before_method(:body)]
      contents.reverse! if mode == :single
      contents.detect { |content| !content.blank? }.to_s.strip
    end
end
```
