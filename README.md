# Nelson Judo Website

## Regular ops - development

Generate static files:
```
docker run --rm -ti -v $PWD:/tmp/code --net=host hugomods/hugo:debian-nightly-non-root bash
cd /tmp/code/src/
hugo server --themesDir=../
```


## Regular ops - generate static website

Generate static files:
```
docker run --rm -ti -v $PWD:/tmp/code --net=host hugomods/hugo:debian-nightly-non-root bash
cd /tmp/code/src/
hugo --gc --minify --themesDir=../
```

Host it locally with Apache:
```
docker run -dit --name my-apache-app -p 8080:80 -v "$PWD/src/public":/usr/local/apache2/htdocs/ httpd:2.4
```

https://gohugo.io/host-and-deploy/host-on-github-pages/

## How the code was generated
* using the Hugo template https://github.com/zjedi/hugo-scroll
* the template code is in `./hugo-scroll`
* copied the [exampleSite](https://github.com/zjedi/hugo-scroll/tree/master/exampleSite) dir as [src](./src)
* https://gohugo.io/getting-started/quick-start/