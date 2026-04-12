# Nelson Judo Website

## Regular ops - development

Generate static files:
```
docker run --rm -ti -v $PWD:/tmp/code --net=host hugomods/hugo:debian-nightly-non-root bash
cd /tmp/code/src/
cp assets/images/* public/images/
cp ../hugo-scroll/assets/js/* public/js/
hugo server --themesDir=../
```

Open your web browser at http://localhost:1313/

## Regular ops - generate static website

Generate static files:
```
docker run --rm -ti -v $PWD:/tmp/code --net=host hugomods/hugo:debian-nightly-non-root bash
cd /tmp/code/src/
hugo --gc --minify --themesDir=../
cp assets/images/* public/images/
cp ../hugo-scroll/assets/js/* public/js/
```

Host it locally with Apache:
```
docker run -dit --name my-apache-app -p 8080:80 -v "$PWD/src/public":/usr/local/apache2/htdocs/ httpd:2.4
```

Open your web browser at http://localhost:8080/


https://gohugo.io/host-and-deploy/host-on-github-pages/

## How the code was generated
* using the Hugo template https://github.com/zjedi/hugo-scroll
* the template code is in `./hugo-scroll`
* copied the [exampleSite](https://github.com/zjedi/hugo-scroll/tree/master/exampleSite) dir as [src](./src)
* https://gohugo.io/getting-started/quick-start/