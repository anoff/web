# anoffs github pages

based on [resumecard](https://ddbullfrog.github.io/resumecard)

## usage

To run jekyll locally without having to install everything

```sh
docker run --rm --label=jekyll --volume=$(pwd):/srv/jekyll -it -p 127.0.0.1:4000:4000 jekyll/jekyll jekyll serve
```
