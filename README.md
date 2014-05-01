# assemble-contrib-anchors [![NPM version](https://badge.fury.io/js/assemble-contrib-anchors.png)](http://badge.fury.io/js/assemble-contrib-anchors)

> Assemble plugin for creating anchor tags from headings in generated html using Cheerio.js.

## Quickstart
In the command line, run:

```bash
npm install assemble-contrib-anchors --save
```

Next, register the plugin with Assemble in your project's Gruntfile:

```js
assemble: {
  options: {
    plugins: ['assemble-contrib-anchors', 'other/plugins/*']
  }
}
```

## Options
#### template

Specify a custom template (Underscore/Lo-Dash) to use for anchor markup. This is the default template:

```js
module.exports = [
  '<a href="#<%= id %>" name="<%= id %>" class="anchor">',
  '  <span class="anchor-target" id="<%= id %>"></span>',
  '  <span class="glyphicon glyphicon-link"></span>',
  '</a>'
].join('\n');
```

To use a custom template just specify it in the options as follows:

```js
assemble: {
  foo: {
    options: {
      plugins: ['assemble-contrib-anchors'],
      function (name, options) {
    var opts = _.extend({}, verb.options, options || {});
    return verb.utils.safename(name, opts);
  }: {
        template: './path/to/custom/template.js'
      }
    },
    files: {'dist/': 'content/*.md'}
  }
}
```


Visit the [plugins docs](http://assemble.io/plugins/) for more info or for help getting started.

## Examples
### Configuration

You can also use the plugin with specific targets:

```js
assemble: {
  foo: {
    options: {
      plugins: ['assemble-contrib-anchors'],
      layout: 'blog-post.hbs'
    },
    files: {'dist/': 'content/*.md'}
  },
  // The plugin won't run on this target
  bar: {
    files: {'dist/': 'templates/*.hbs'}
  }
}
```

To disable the plugin, either remove it from the options or specify `function (name, options) {
    var opts = _.extend({}, verb.options, options || {});
    return verb.utils.safename(name, opts);
  }: {convert: false}` in the options:

```js
assemble: {
  foo: {
    options: {
      plugins: ['assemble-contrib-anchors'],
      function (name, options) {
    var opts = _.extend({}, verb.options, options || {});
    return verb.utils.safename(name, opts);
  }: {convert: false}
    },
    files: {'dist/': 'content/*.md'}
  }
}
```

### Before

```html
<h1 id="glyphicons">Glyphicons</h1>
```
### After

```html
<h1 class="docs-heading">
  <a href="#heading-id-name" name="heading-id-name" class="anchor">
    <span class="anchor-target" id="heading-id-name"></span>
    <span class="glyphicon glyphicon-link"></span>
  </a>
  Glyphicons
</h1>
```
Currently the plugin adds [Bootstrap](http://getbootstrap.com/components/#glyphicons) glyphicon classes. If you want to use different classes, find a bug, or have a feature request, [plesae create an issue](https://github.com/assemble/assemble-contrib-anchors/issues/new)

### Example

[![image](https://f.cloud.github.com/assets/383994/1511486/c2414c4e-4aaf-11e3-9c16-30f2993ae2d7.png)](http://assemble.github.io/example-assemble-anchors/components.html#glyphicons)

Visit the [anchors example repo](https://github.com/assemble/example-assemble-anchors).


## Assemble plugins
Here are some related projects you might be interested in from the [Assemble](http://assemble.io) core team.

+ [assemble-contrib-contextual](https://github.com/assemble/assemble-contrib-contextual): Generates a JSON file containing the context of each page. Basic plugin to help see what's happening in the build. 
+ [assemble-contrib-decompress](https://github.com/assemble/assemble-contrib-decompress): Assemble plugin for extracting zip, tar and tar.gz archives.  
+ [assemble-contrib-download](https://github.com/assemble/assemble-contrib-download): Assemble plugin for downloading files from GitHub. 
+ [assemble-contrib-lunr](https://github.com/assemble/assemble-contrib-lunr): Assemble plugin for creating a search engine within your static site using lunr.js. 
+ [assemble-contrib-markdown](https://github.com/assemble/assemble-contrib-markdown): Convert markdown files to HTML using marked.js. This plugin is an alternative to Assemble's markdown Handlebars helpers. Both are useful in different scenarios. 
+ [assemble-contrib-permalinks](https://github.com/assemble/assemble-contrib-permalinks): Permalinks plugin for Assemble, the static site generator for Grunt.js and Yeoman. This plugin enables powerful and configurable URI replacement patterns, presets, uses Moment.js for parsing dates, and much more. 
+ [assemble-contrib-sitemap](https://github.com/assemble/assemble-contrib-sitemap): Sitemap generator plugin for Assemble 
+ [assemble-contrib-toc](https://github.com/assemble/assemble-contrib-toc): Create a table of contents in the generated HTML, using Cheerio.js 
+ [assemble-contrib-wordcount](https://github.com/assemble/assemble-contrib-wordcount): Assemble plugin for displaying a word-count on blog posts or pages. 

Visit [assemble.io/plugins](http:/assemble.io/plugins/) for more information about [Assemble](http:/assemble.io/) plugins.


## Contributing
Find a bug? Have a feature request? Please [create an Issue](https://github.com/assemble/assemble-contrib-anchors/issues).

In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality,
and run `docs` in the command line to build the docs with [Verb](https://github.com/assemble/verb).

Pull requests are also encouraged, and if you find this project useful please consider "starring" it to show your support! Thanks!

## Author

**Brian Woodward**

+ [github/doowb](https://github.com/doowb)
+ [twitter/doowb](http://twitter.com/jonschlinkert)

## License
Copyright (c) 2014 Brian Woodward, contributors.  
Released under the MIT license

***

_This file was generated by [grunt-verb](https://github.com/assemble/grunt-verb) on May 01, 2014._
