Earthquake
====

Twitter Client on Terminal with Streaming API.

It supports ruby 1.9 only.

Install
----

    gem install earthquake

Usage
----

### Launch

    $ earthquake

Commands
----

### Tweet

    ⚡ Hello World!

### Searth

    ⚡ :search #ruby

### Eval

    ⚡ :eval Time.now

### Exit

    ⚡ :exit

### Restart

    ⚡ :restart

And there are more commands!

Customize
----

The config file is '~/.earthquake/config'.

### Changing the colors

    Earthquake.config[:colors] = (31..36).to_a - [34]

The blue is excluded.

### Running on debug mode

    Earthquake.config[:debug] = true

デバッグモードで動作しているとき、コードの修正は即座に反映される（正確にはコマンドの実行の直前にリロードされる）。

### Defining your commands

#### A command named 'foo':

    Earthquake.init do
      command :foo do
        puts "foo!"
      end
    end

#### Handle the command args:

    Earthquake.init do
      command :hi do |m|
        puts "Hi #{m[1]}!"
      end
    end

The 'm' is a MatchData.

#### Using regexp:

    Earthquake.init do
      # Usage: :add 10 20
      command %r|^:add (\d+)\s+(\d+)|, :as => :add do |m|
        puts m[1].to_i + m[2].to_i
      end
    end

TODO
----

* filter
* plugin system
* keyword tracking
* more intelligent completion
* spec
* typable id

Copyright
----

Copyright (c) 2011 jugyo. See LICENSE.txt for further details.