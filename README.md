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
Change baseURL=tzchat=tzchat to your github site
```
echo "baseURL=tzchat=tzchat = 'https://bitc0m.github.io/tzchat'" >> ./config.toml
```
Add publish directory to config.toml
```
publishDir = "docs"
```
 
## Build submodules
Get the submodules.
```
git submodule add -b master "git@work.github.com:bitc0m/tzchat-pages.git" public
git checkout --orphan gh-pages
git reset --hard
git commit --allow-empty -m "Initializing gh-pages branch"
git push upstream gh-pages
git checkout master
rm -rf public
git worktree add -B gh-pages public origin/gh-pages
 hugo
 cd public && git add --all && git commit -m "Publishing to gh-pages" && cd ..

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
