# GHCSCW Developer Quick Start Guides

## NetCore 3 Central Template

.NET Core 3.0

https://docs.microsoft.com/en-us/aspnet/core/fundamentals/?view=aspnetcore-3.0&tabs=windows

<!--
A _Docsify_ doc site works works _without_ the need to edit your existing docs and _without_ building any HTML pages. The rendering is done on the client-side in a single page application, running on _index.html_.

Files needed to build a docs site with _Docsify_:

- **cover page** - Optional landing page with background color or image and some minimal text.
- **homepage** - First page that a user sees, after the cover page.
- **sidebar** - Describes your menu layout. As _Docsify_ is not aware of directory structure so it may not function as you hope without this file.
- **index page** - Base of the app. This will setup the app using the _Docsify_ library, set a theme and apply other configurations.

Once you have that setup in _docs_ directory and have pushed to Github, you can setup Github Pages serving the _docs_ directory. Note: _Docsify_ also works with _Netlify_ as per their docs, but this project just considers the Github Pages case.

-->

The NETCore3CentralTemplate aims to be a platform on which to build reliable and maintainable console applications.  The template is wired-up for simple data extracts all the way to those applications with continually growing complexities.   This template also moves our C# technology stack forward in the ever changing .Net landscape.

Technologies

- VS 2019 - .Net Core 3.0 comes built in.
- .NET Core 3.0 Console Application with .NET Standard 2.1 Class Libraries
- Dapper – Micro Object Relational Mapper
- Xunit – C# Testing Framework
- GHCDataAccessLayer – Extended

.NET Core 3.0 - Utilized Features

Dependency Injection

- Provides loose couplin g between objects.
- Allows for easier and more extensive unit testing.
- https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-3.0

Configuration

- Control application and data access settings through appsettings.json
- appsettings.json -> Options -> AppSettings.cs = strongly typed configuration

https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-3.0

Logging

- Logging is ready to go and is too easy to get it wherever you need it.
- https://docs.microsoft.com/en-us/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0

Testing

- Visual Studio Test Explorer integration with Xunit.
- https://docs.microsoft.com/en-us/dotnet/core/testing/unit-testing-with-dotnet-test

### 1. Machine Setup for NUGET

https://github.com/microsoft/artifacts-credprovider#azure-artifacts-credential-provider

### 2. Installing/Uninstalling the template

Dotnet EnvironmentVariable????
Install:

```
dotnet new -i CentralTemplateConsoleApp

dotnet new -i CentralTemplateSolution
```

If we were to update the template and you want the latest version. Run the below code to uninstall the template.

Uninstall:

```
dotnet new -u CentralTemplateConsoleApp

dotnet new -u CentralTemplateSolution
```

Then run the install command again to get the updated template.

### 3. View Installed .Net Core Templates

```
dotnet new --list
```

### 4. Central Template Template Solution

```
https://dev.azure.com/GHCSCW/Business%20Solutions/_git/NETCore3CentralTemplate
```

### 5. Central Template Template Solution

```
https://dev.azure.com/GHCSCW/Business%20Solutions/_git/NETCore3CentralTemplateConsoleApp
```

```bash
$ cd docsify-template
```

## Create new Solution From Template

When starting with a new solution follow the below steps to use the template. Creating a new project from the template

### 1. CD to your repos folder

### 2. Create Solution

```
dotnet new centralsolution -n NewSolutionName
```

Your new template should be built and in the location you were in. It will build your solution file for you.

### 2. Run

#### 2.1 Serve

Start running a local server to preview your site.

Here are some options below, otherwise there is a much longer list [here](https://gist.github.com/willurd/5720255).

- From docs directory.
  ```bash
  $ cd docs
  $ python3 -m http.server 3000
  $ python2 -m SimpleHTTPServer 3000
  ```
- From project root.
  ```bash
  $ # Requires Docsify CLI.
  $ docsify serve docs
  ```

You can also add aliases to either your `~/.bashrc` or `~/.aliases` files to make them quick to use across projects.

```bash
alias pserve='python3 -m http.server 3000'
alias docs='docsify serve docs'
```

#### 2.2 View

Then open http://localhost:3000 in the browser.

User notes:

- When viewing the site, if you scroll down far enough you will see a hamburger menu which lets you dynamically open or close the sidebar.

## Setup your own docs site

This tutorial is based on the _Docsify_ [Quickstart](https://docsify.js.org/#/quickstart) guide, but rather than giving snippets of file this tutorial lets you copy entire template files to your project, there are `TODO` items in the templates making it clear what to edit. Plus in the template, there are some useful or pretty configurations which have been set after investigating the configurations guide and trying them out on my own project.

Follow to steps in this section copy a base structure and configs from this project to your own, then customize them for your needs.

### 1. Get this project locally

Clone this template repo to your machine using the [steps](#get-a-local-copy-of-this-repo) above, so you can use it copy files from later.

### 2. Create base structure

Navigate to your existing project's `docs` directory.

```bash
$ cd <PATH_TO_YOUR_REPO>/docs
```

Create a file for Github Pages to use. This can remain empty - its existence just tells Github Pages to include the underscore files in builds.

```bash
$ touch .nojekyll
```

Copy the template files from the template project's _quickstart_ directory to your own project.

```bash
$ cp <PATH_TO_TEMPLATE_REPO>/quickstart/* .
```

Start serving your docs folder now even though it is incomplete. Then, as you follow the customization steps below, you can check to see what changes on the frontend.

### 3. Configure homepage

Edit the _docs/README.md_ homepage. Complete the `TODO` items, using the suggestions in this section.

- Anything outside of your _docs_ directory will **not** be served online. Therefore you might want copy the the content from your project root's _README.md_ to the _docs/README.md_. After that, you might want to make the root _README.md_ very short, if you don't want to worry about keeping two identical files in sync.
- You might want to opt for short _docs/README.md_ file if you prefer to put more documentation in other _docs_ files.
- Note that you are not required to put in links to other docs file within your _docs/README.md_ file. As that is what the _Docsify_ sidebar. If you do put in any links in _docs/README.md_, they must be **relative** to the _docs_ directory such as `file.md`, as absolute URLs such `/docs/file.md` will not work within the _docs_ site.

### 4. Configure menu structure

#### Doc links

If you have put links from one of your doc files to another, you might have to edit your existing doc files to avoid the links breaking when viewed as docs site.

References should be relative to the _docs_ directory not to the file itself, even if a file is inside a directory within _docs_. This is unlike the expected of markdown.

Any link references which start as `docs/file.md` or `/docs/file.md` will cause errors, because the server is only aware of directories within _docs_.

#### Sidebar

The sidebar is the menu page on the left of the docs and shows on all pages.

If you **do not** want to configure a sidebar, delete _\_sidebar.md_ from your _docs_ directory, set the sidebar option to `false` in _index.html_ and skip to the next section.

If you **do** have files in your _docs_ directory you want to appear in the menu page, then edit the _\_sidebar.md_ file. The format should be markdown bullet points which can be nested. Include links to you files - note that paths are relative to docs directory.

Here is an example sidebar config:

```markdown
- [Foo](foo.md)
- [Bar](bar.md)
- Baz
  - [Fizz](baz/fizz.md)
  - [Foo Bar](baz/foobar.md)
```

##### Sidebar without config

You could have a sidebar enabled in _index.html_, but without sidebar config set (empty file or no file). Then your index page will use its **own** page outline as the menu. But with no access to subpages, as _Docsify_ is not aware of them\_.

You may even **want** your entire site to be a single page based on _README.md_ content and no other doc files. As you will get the benefit of the look of a single page site and any section headings added to your menu will be added to your menu pane automatically (no need to maintain a sidebar file).

##### Link to homepage

The button at the top of sidebar is a link to site's root path. This will be the cover page, if you have one.

If you a menu button which takes you to the homepage rather, add an item which has a reference to the root path plus with the ID of the heading of _docs/README.md_.

e.g.

```
- [Home](/#my-project)
```

### 5. Configure cover page

The cover page is the first page that a visitor sees before scrolling down to the homepage.

If you want to use it, edit your _docs/\_coverpage.md_ file and complete the `TODO` items. You can also use this project's [cover page](https://raw.githubusercontent.com/MichaelCurrin/docsify-template/master/docs/_coverpage.md) on Github as a reference.

You can add additional buttons to the bottom of the homepage, but there should be no gaps between the lines in your file. And the last one will be solid while the others will be transparent.

The _Docsify_ site explains how to set a background image or color [here](https://docsify.js.org/#/cover?id=custom-background). A background image should come _after_ the buttons in your file, as _Docsify_ looks for an image there then uses CSS to place the image behind the content and give it faded grey look.

You can delete the cover page and disable it in _index.html_.

#### Image

You could include an image (logo, photo) above your project title. For example, you could do this if you have a file in a _docs/\_media_ directory.

```
![icon](_media/logo.svg)
```

### 6. Configure Style

Edit _index.html_.

#### 6.1 Color

Optionally set a theme color. This affects how some content looks, such as quoted blocks, underlined text and buttons. This will default to theme's default if not set manually. i.e. green for _Vue_ and blue for _Buble_.

```js
window.$docsify = {
  themeColor: "#3F51B5"
};
```

More on Docsify [theme color](https://docsify.js.org/#/configuration?id=themecolor).

#### 6.2 Themes

Find the style which is set in the `<head>` tag, which looks like this.

```html
<link rel="stylesheet" href="//unpkg.com/docsify/lib/themes/<THEME>" />
```

Replace the end of URL with one of these four themes.

- `vue.css`
- `buble.css`
- `dark.css`
- `pure.css`

You can optionally remove `/lib` from the theme URL to get the _uncompressed_ CSS file.

More on Docsify [themes](https://docsify.js.org/#/themes?id=themes) guide.

### 7. Advanced configuration

This advanced section is optional, so can be skipped.

The configuration steps above already get you a prettier and more usable site in my opinion than the barebones one which the _Docsify_ `init` command or their _Quickstart_ guide gives you.

If you want to do further configuration, I recommend you look at the _Docsify_ [Configuration](https://docsify.js.org/#/configuration) page.

There are some useful things there in like adjusting the sidebar levels, putting a logo in the sidebar or setting your root _README.md_ as your homepage. There is even a search bar you can add to site.

If you want know a summary view of what the defaults are for the app on `index.html`, see the _Docsify_ [config.js](https://github.com/docsifyjs/docsify/blob/develop/src/core/config.js) script.

## Setup Github Pages site

If you followed the steps above, you'll have a locally running docs site.

Now, commit and push the files to Github.

Next, edit your repo's setting on Github. Select the option to serve the `docs` directory of the `master` branch as Github Pages site. When you refresh the settings page, then you will see a link to your site there.

Open the link in the browser.

## Docsify CLI

The CLI tool is optional. It can be used to do the following.

- `docsify init docs`: Setup an initial _README.md_ (duplicated from project root), _index.html_ and _.nojekyll_ in your a target directory. If you don't want the CLI to do it for you, you can create the files by hand or use this project's _quickstart_ directory to get you going.
- `docsify serve docs`: Serve the target directory as docs site locally, with hot reload for if you save any file changes. See [server](#21-serve) options above.

View the Docsify [Quickstart](https://docsify.js.org/#/quickstart) guide for how to install the CLI in your global node packages and then to use it.

## Why not a static site generator?

These are just tools to build a site. What is appropriate depends on your use case, how much you need to customized the site and how much effort you want to spend on installing/running/maintaining the project. I found a static site generator is not a good fit for when I want to build a light docs site around existing docs directories in my projects.

Jekyll and Hugo are options for static site generators which can use themes suited to documentation and they can build off of a docs directory. If you want to read more about those, see my [resources](https://github.com/MichaelCurrin/static-sites-generator-resources) project.

A static site generator can be heavy...

There are dependencies to manage - they might have to be upgraded if their are security vulnerabilities or they are no longer available. Such as plugins and themes for _Jekyll_. And plugins for _Hugo_. Plus you probably need a couple of _JavaScript_ or _CSS_ files that either you or a theme added. Such as _Query_. This _Docsify_ project only needs exactly one _JavaScript_ and one _CSS_ file.

There is HTML to build locally and on the remote. While _Docsify_ needs no dependencies to serve a site, _Jekyll_ sites needs `jekyll` installed and _Hugo_ sites need `hugo` available.

A static site needs to to customize it in depth or setup a theme which also takes effort. You may lose or gain functionality when switching between Jekyll themes because they use their own templates and layouts.

You probably have to add _front matter_ to your doc files so they can inherit from layouts and have the correct metadata like title.

As with _Docsify_, you will probably have to create a config file which covers the structure of your project for use in the sidebar.

Unlike building static files with HTML, with with Docsify there is a single page application running off of a _index.html_ - on each request, a markdown file is fetched by the client and rendered as HTML with a theme and menu. The performance will depend more on the server when serving static HTML pages (prebuild and serve page on the client) or on the client when using a single page application (build structure on the client).

Also, the _Docsify_ approach will only work if JavaScript is enabled.

The _Docsify_ site says it supports back to Internet Explorer 11, so that at least helps for a wider audience of users.

Although SEO crawlers can do better at sites like single page application, _Docsify_ is still said not to be SEO-friendly, compared with static sites where all HTML is pre-rendered.
