# Liquid Drops

Drops let you provide the user with custom functionality. They're very much like a standard Ruby class, but have all un-needed and potentialy dangerous methods removed. From the user's perspective a drop acts very much like a Hash, thought methods are accessed with dot-notation aswell as element selection. A drop method cannot be invoked with arguments. Drops are called just-in-time thus allowing you to lazily load objects.

## Standard drop methods:

before_method(method):

Called once for every invokation, even if the destination method doesn't exist. Can be used to provide dynamically named methods.

Example:

    class MembersDrop < Liquid::Drop

      def before_method(method)
        user = User.find_by_name(method)
        user ? UserDrop.new(user) : nil
      end

    end

### View

    {% assign user = members.ian %} {{ user.name }}

invoke_drop(method):

Called by liquid to invoke the target drop method.

has_key(name):

Currently returns true regardless.

to_liquid:

Returns the drop instance.

### Drop usage:

    class ProductDrop < Liquid::Drop

      def initialize(product)
        @product = product
      end

      def name
        @product[:name]
      end

      def description
        @product[:description]
      end

      def price
        @product[:price]
      end

    end

### Controller 

    template = Liquid::Template.parse( File.read( product_view.liquid ) ) template.render( { :product => ProductDrop.new(@product) } )

### View

    Viewing product: {{ product.name }} <br/><br /> {{ product.description }} <br /> £{{ product.price }} 