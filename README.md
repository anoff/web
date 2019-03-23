# Andreas' landing page

## Local preview

```sh
docker run --rm -v $PWD:/app -p 1313:1313 anoff/hugo-asciidoctor hugo server -D --bind 0.0.0.0
```

## Deployment

```sh
# generate the static site
docker run --rm -v $PWD:/app anoff/hugo-asciidoctor hugo --gc --minify -d _site
```
