# blog

my weblog

## How to setup

requirements:

- rbenv
- ruby-build
- rbenv-gem-rehash

install Ruby 2.1.1 by rbenv:

```sh
$ rbenv install 2.1.1
```

install bundler and install required gems by bundler:

```sh
$ echo 'gem: --no-document' >> $HOME/.gemrc
$ gem install bundler
$ rake install
```

## Rakefile tasks

- build
  - build blog
- install
  - install required gems
- new (default task)
  - create new post
- preview
  - preview in local
