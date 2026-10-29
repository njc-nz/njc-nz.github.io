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

## Local environment setup

### To edit website files locally
1. Install [git](https://git-scm.com/install/) for code files versioning. It's a CLI tool.
1. Sign up at GitHub.com.
1. Check that you can see https://github.com/njc-nz/njc-nz.github.io in your web browser, and that you can download it with `git clone`.
1. Install [git-cola](https://git-cola.github.io/) or a similar tool, to get a GUI for git. 
1. Install an IDE of choice (e.g. Visual Studio Code) to read and edit the code files easily.
1. Try and edit some contents, e.g. edit text in here `src/content/en/homepage/events.md`.

### To get a local preview of the website
* Either install [docker](https://www.docker.com/) to run Hugo in an isolated environment (in a sandbox)
* Or install [Hugo](http://gohugo.io/installation/) directly on your machine

Using docker is safer (because it provides an isolated environment) and more reliable (because we can lock versions of selected software). Installing Hugo directly is easier.

### To push the changes
#### For a review
When you are happy with your changes, and you **don't** want the changes to be automatically deployed (because you want someone else to review them first), commit your changes to a separate git branch:
```
# create a new git branch, name it so that you remember what changes you made
git checkout -b new-timetable-2026-august

# commit your changes
# either use git-cola GUI here or git CLI

# push your changes to the newly created git branch
git push origin new-timetable-2026-august
```

#### For an automated deployment
When you are happy with your changes, and you want the changes to be automatically deployed, commit and push them. Use Git-Cola for commit, and then `git push` for push.

## How the code was generated
* using the Hugo template https://github.com/zjedi/hugo-scroll
* the template code is in `./hugo-scroll`
* copied the [exampleSite](https://github.com/zjedi/hugo-scroll/tree/master/exampleSite) dir as [src](./src)
* https://gohugo.io/getting-started/quick-start/

