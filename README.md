# markdown-post-parser

Parser for building blogs in Markdown.

## Install

Add modules to `dependencies`.

```js
{
  ...
  "dependencies": {
    ...
    "markdown-post-parser": "git+https://github.com/kimulaco/markdown-post-parser.git",
    ...
  }
  ...
}
```

Install the module with `npm` or `yarn`.

```shell
npm install
```

## Use

### CLI

```shell
mpp -m index.md -i ./src -o ./json/blog.json -s ./static
```

### API

```js
const MarkdownPostParser = require('./markdown-post-parser')
const markdownPostParser = new MarkdownPostParser({
  main: 'index.md',
  input: './src',
  output: './json/blog.json',
  static: './static'
})

markdownPostParser.generate()
```

## Example

### Directory

```
src
├─ post-01
│  ├─ index.md
│  └─ example.png
├─ post-02
│  └─index.md
└─ post-02
   └─index.md
```

### Markdown format

src/post-01/index.md

```
---
id: post-01
title: Example Post
description: test post
created_at: "2019-04-01"
updated_at: "2019-04-02"
tags:
  - HTML
  - CSS
  - JavaScript
---

## overview

text
```

### JSON format

```js
{
  // All posts
  "posts": [
    {
      "path": "test/src/post-01",
      "main": "test/src/post-01/index.md",
      "id": "post-01",
      "title": "Example Post",
      "description": "test post",
      "created_at": "2019-04-01",
      "updated_at": "2019-04-01",
      "tags": [
        "HTML",
        "CSS",
        "JavaScript"
      ],
      "body": "<h2>overview</h2>\n<p>text</p>\n",
      "resource": [
        "test/src/post-01/example.png"
      ]
    },
    ...
  ],

  // All tags
  "tags": [
    "HTML",
    "CSS",
    "JavaScript",
    ...
  ]
```

## Development

```shell
# Unit test
npm run test
```

## ToDo

- Test code.
- Copy static resource.
- Watch option.
- Publish npm.

## License

[MIT](https://github.com/kimulaco/markdown-post-parser/blob/master/LICENSE)
