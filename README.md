Emanuele Ghelfi's personal web site at [http://emanueleghelfi.github.io/](http://emanueleghelfi.github.io/).

The site uses the [Beautiful Jekyll](http://deanattali.com/beautiful-jekyll) theme provided by Dean Attali.

## For me

### Ruby configuration

```bash
rvm use ruby-2.6.3 --default
```

### Local deploy

```bash
bundle exec jekyll serve [--drafts]
```

### Build

```bash
bundle exec jekyll build
```

### After build

```bash
cp CNAME _site
```

### Deploy

```
rake commit_deploy
```
