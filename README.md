# Megaphone

Dynamic notification system for rails 3.

## Installation

Add this line to your application's Gemfile:

    gem 'megaphone'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install megaphone

## Usage

Once installed, add the following line to the model you want to receives messages

    include Megaphone::Notifiable

Example:

    class User
      include Megaphone::Notifiable

      # your code here
    end

and then, User has many messages, use it like any other has_many relationship

    User.last.messages.first
    # => nil
    User.last.messages.create! title: 'A Title', text: 'A text'
    # => true
    User.last.messages.first
    # => #<Megaphone::Message>

Also, some basic helper methods were added to the model

    User.last.has_unread_messages?
    # => true
    User.last.unread_messages_count
    # => 4

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
