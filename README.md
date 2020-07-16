# tzchat-web
Content for tzchat.org website, built using Hugo (static site generator).

## Initial setup
Install the Hugo toolchain.
```
brew install hugo
```

Clone the tzchat repo locally.
```
git clone https://github.com/tezos-commons/tzchat.git
cd tzchat
```

## Set config 
Change baseURL in config.toml to your deployment site
```
baseURL="https://bitc0m.github.io/tzchat"
```

## Build submodules
Get the submodules.
```


git submodule update --init --recursive
```

## Domain
ref: https://medium.com/@hossainkhan/using-custom-domain-for-github-pages-86b303d3918a#:~:text=Go%20to%20your%20GitHub%20Pages,Don't%20delete%20it.
Create ./CNAME
```
staging.tzchat.org
```
Test with
```
dig staging.tzchat.org +nostats +nocomments +nocmd
```

## Serve dev version of site

```
hugo server -D
```

Look in the server output for a message like `Web Server is available at http://localhost:1313/`, and visit that URL in a browser.
