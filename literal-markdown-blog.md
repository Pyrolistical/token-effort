# Literal markdown blog

[Token Effort](https://pyrolistical.github.io/token-effort/) · [Markdown](https://pyrolistical.github.io/token-effort/literal-markdown-blog.md)

Publish a blog whose pages are markdown an agent can build from

- Every post is a spec an agent can build from
- Pages read as styled text while showing their raw markdown
- Copying or fetching a page gives its exact markdown

## Implementation

- Line-by-line markdown renderer
- `<pre>` with `white-space: pre-wrap`
- `font-size: 0` on link syntax
- `<link rel="alternate" type="text/markdown">`
- Orphan `gh-pages` branch
- GitHub Pages

## Polish

- Page
  - Dim syntax so text reads first
  - Hide only link and image syntax
  - Solarized following the system setting
  - Hang wrapped list items under their text
  - Lone image shown in place
  - Inline image as a normal link
  - Keep backgrounds on wrapped code
  - Stop mobile browsers resizing text
- Post
  - Title, optional screenshot, purpose, specs, then optional implementation, polish and related posts
  - Screenshot with fake data
  - Homepage and markdown links under the title
  - Last modified from git
- Build
  - Pages, homepage and feed from committed sources
  - Fail on uncommitted changes
  - Fail on a relative link
  - Fail on a missing screenshot
  - Fail on an unclosed code fence
  - Fail on an unknown related post
- Distribution
  - Homepage grouped by category
  - RSS feed
  - Assets named by content hash
  - Absolute URLs everywhere

Last modified 2026-11-03
