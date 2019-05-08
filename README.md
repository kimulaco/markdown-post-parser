# markdown-post-parser

Parser for building blogs in Markdown.

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
│  ├─index.md
│  └─ example.png
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
updated_at: "2019-04-01"
tags:
    - HTML
    - CSS
    - JavaScript
---

## overview

text text

- list item
- list item
- list item
- list item
```

### JSON format

```js
{
  // All posts
  "posts": [
    {
      "path": "src/post-01",
      "main": "src/post-01/index.md",
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
        "src/post-01/example.png"
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
  ],

  // All resources
  "resources": [
    "src/post-01/example.png",
    "src/post-02/example.png"
  ]
```

## Development

```shell
# Build TypeScript
yarn build

# Development mode
yarn dev

# Unit test
yarn test
```

## License

[MIT](https://github.com/kimulaco/markdown-post-parser/blob/master/LICENSE)
