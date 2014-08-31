# Substrata

Substrata is a tiny manager of template continuity.  It consists of three individual services, and a core domain shared between them all:
* Courier - This is a gateway to any given service provider.  It is extensible to any given service, but each service requires a class which conforms to the provided interface guidelines.
* Composer - A tool for building, previewing and editing templates.  It is mostly self-contained, and utilizes the ACE editor in order to accomplish its goals.
* Dispatcher - This is the final piece.  It provides an API which abstracts the above two services into a single endpoint.  Hit the endpoint with the information for the service, and the parameters to render the template with, and Dispatcher handles the rest.

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'substrata'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install substrata

## Usage

Substrata is intended to be simple and easy to use.  It is pluggable into Rails, by mounting `Substrata::Courier`, `Substrata::Composer`, or `Substrata::Dispatcher` apps.  It can also be mounted in Sinatra, or it can be mounted in a straight up `config.ru` file.

The one caveat is Dispatcher.  The nature of Courier and Composer is that they are entirely unaware of one another and their environment.  Dispatcher's purpose is to know about the different pieces of Substrata.  You will need to configure Dispatcher to be aware of how to interact with its different pieces - a small API is provided to tell it how to contact the Courier and Composer.

Wherever Dispatcher is initialized, configure it:

```ruby
Substrata::Dispatcher.configure do
  courier  at: "uri://to.courier"
  composer at: "uri://to.composer"
end
```

## Contributing

1. Fork it ( https://github.com/[my-github-username]/substrata/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
