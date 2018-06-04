# `react-markdown-github`

A React component that wraps [react-markdown] that:
-  links all headers with an anchor link.
-  resolves all relative links to absolute Github URLs based on the sourceUrl of the document.
    - e.g. /foo/bar.md becomes https://github.mycorp.com/org/component/blob/master/foo/bar.md
-  allows the parent component to override the resolved url.

## Installation

``` bash
npm install react-markdown-github
```

## Usage

```js
<MarkdownGithub 
  source={ markdown } 
  sourceUrl='https://github.mycorp.com/org/component/blob/master/README.md'  
  resolver={ ({ url, github, org, repo, filename }) => { } }
  transformImageUri={ ({ url, github, org, repo, filename }) => {} }
  renderers={ code: myCodeFormatter } 
  className='myClass' />
```

## Component Properties

- `sourceUrl` Absolute URL to orgional markdown. All relative links will be
  resolved relative to this URL.
- `resolver` URL resolver function. To override the URL resolver and point a url
  to an alternate location.
- `transformImageUri` image URL resolver function. Default behavior is to not modify image urls.
- `renderers` An object of render function values with keys corresponding to
  [Node Type][react-markdown-node-types] to be passed to [react-markdown].
- `className` the CSS class passed to [react-markdown].

## Test

``` bash
npm test
```

##### LICENSE: [MIT](/LICENSE)

[react-markdown]: https://github.com/rexxars/react-markdown
[react-markdown-node-types]: https://github.com/rexxars/react-markdown/blob/master/README.md#node-types
