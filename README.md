abstract_type
==============

[![Gem Version](https://badge.fury.io/rb/abstract_type.png)][gem]
[![Build Status](https://secure.travis-ci.org/dkubb/abstract_type.png?branch=master)][travis]
[![Dependency Status](https://gemnasium.com/dkubb/abstract_type.png)][gemnasium]
[![Code Climate](https://codeclimate.com/github/dkubb/abstract_type.png)][codeclimate]
[![Coverage Status](https://coveralls.io/repos/dkubb/abstract_type/badge.png?branch=master)][coveralls]

[gem]: https://rubygems.org/gems/abstract_type
[travis]: https://travis-ci.org/dkubb/abstract_type
[gemnasium]: https://gemnasium.com/dkubb/abstract_type
[codeclimate]: https://codeclimate.com/github/dkubb/abstract_type
[coveralls]: https://coveralls.io/r/dkubb/abstract_type

This is a small standalone gem featuring a module ripped out from [veritas](https://github.com/dkubb/veritas).
It allows to declare abstract_type classes and modules in an unobstrusive way.

Installation
------------

With Rubygems:

```bash
$ gem install abstract_type
$ irb -rubygems
>> require 'abstract_type'
=> true
```

With git and local working copy:

```bash
$ git clone git://github.com/dkubb/abstract_type.git
$ cd abstract_type
$ rake install
$ irb -rubygems
>> require 'abstract_type'
=> true
```

Examples
--------

``` ruby
class Foo
  include AbstractType

  # Declare abstract instance method
  abstract_method :bar

  # Declare abstract singleton method
  abstract_singleton_method :baz
end

Foo.new  # raises NotImplementedError: Foo is an abstract type
Foo.baz  # raises NotImplementedError: Foo.baz is not implemented

# Subclassing to allow instantiation
class Baz < Foo; end

object = Baz.new
object.bar  # raises NotImplementedError: Baz#bar is not implemented

```

Credits
-------

* Dan Kubb ([dkubb](https://github.com/dkubb))
* Markus Schirp ([mbj](https://github.com/mbj))

Contributing
------------

* If you want your code merged into the mainline, please discuss the proposed changes with me before doing any work on it. This library is still in early development, and the direction it is going may not always be clear. Some features may not be appropriate yet, may need to be deferred until later when the foundation for them is laid, or may be more applicable in a plugin.
* Fork the project.
* Make your feature addition or bug fix.
  * Follow this [style guide](https://github.com/dkubb/styleguide).
* Add specs for it. This is important so I don't break it in a future version unintentionally. Tests must cover all branches within the code, and code must be fully covered.
* Commit, do not mess with Rakefile, version, or history. (if you want to have your own version, that is fine but bump version in a commit by itself I can ignore when I pull)
* Run "rake ci". This must pass and not show any regressions in the metrics for the code to be merged.
* Send me a pull request. Bonus points for topic branches.

Copyright
---------

Copyright &copy; 2009-2013 Dan Kubb. See LICENSE for details.
