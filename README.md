# xrr-233.github.io
A static website for displaying previous projects. The website is based on the remote Jekyll theme [Beautiful Jekyll](https://github.com/daattali/beautiful-jekyll).

## Deployment

### Local test with [Ruby](https://rubyinstaller.org/downloads/) bundler

#### Test whether Ruby is correctly installed

```shell
ruby -v
```

#### Create a new gem file

```shell
bundle init
```

After generating a new gem file, edit it and identify the gems for use in the application.

#### Installing gems

```shell
bundle install
```

#### Start local test (preview)

```shell
jekyll build
jekyll serve
```

## Reference/Acknowledgement

[1] Jekyll local test https://kbroman.org/simple_site/pages/local_test.html

[2] Creating gem file https://stackoverflow.com/questions/30358612/how-to-create-a-gemfile

[3] Ruby 3.0+ with webrick https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll

[4] Remote theme gem structure https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#github-pages-method