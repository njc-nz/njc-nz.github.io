# Nelson Judo Website

## Operations
### Development with a local preview

Use this method for a fast local preview of your changes.

Run the following:
```
docker run --rm -ti -v $PWD:/tmp/code --net=host hugomods/hugo:debian-nightly-non-root bash
cd /tmp/code/src/
cp assets/images/* public/images/
cp ../hugo-scroll/assets/js/* public/js/
hugo server --themesDir=../
```

The [hugo server](https://gohugo.io/commands/hugo_server/) command above creates a long-running process. It launches a local web server which builds and serves the project. Thanks to that, we can see the website preview in a web browser at http://localhost:1313/

### Generating a static website to be hosted online

Use this method to build the project and generate the static files. These exact static files will be later hosted oline.

Run the following:
```
docker run --rm -ti -v $PWD:/tmp/code --net=host hugomods/hugo:debian-nightly-non-root bash
cd /tmp/code/src/
hugo --gc --minify --themesDir=../
cp assets/images/* public/images/
cp ../hugo-scroll/assets/js/* public/js/
```

Now, you can:
1. Either preview it locally. You can host the static files locally with Apache:
```
docker run -dit --name my-apache-app -p 8080:80 -v "$PWD/src/public":/usr/local/apache2/htdocs/ httpd:2.4
```
You can see it in your web browser at http://localhost:8080/

2. Or you can push the changes to GitHub, so that it is hosted with [GitHub Pages](https://gohugo.io/host-and-deploy/host-on-github-pages/). To push changes, you need to `git commit` and `git push` them.



## How the code was generated
* using the Hugo template https://github.com/zjedi/hugo-scroll
* the template code is in `./hugo-scroll`
* copied the [exampleSite](https://github.com/zjedi/hugo-scroll/tree/master/exampleSite) dir as [src](./src)
* https://gohugo.io/getting-started/quick-start/

