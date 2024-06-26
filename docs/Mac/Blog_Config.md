---
description: set up doucsaurus blog
keywords: [docusaurus, blog, cloudfare]
---

# [Blog] Config

## Docusaurus

> **the most helpful way to learn something is reading docs**

### install

pls refer to [docusaurus](https://docusaurus.io/docs/installation)

```bash
# need install node.js
npx create-docusaurus@latest my-blog classic
# then
cd my-blog
npx docusaurus start
```

Open `http://localhost:3000` and follow the tutorial.

### config

Project structure: generated by docusaurus

```bash
my-blog
├── blog
│   ├── 2019-05-28-hola.md
│   ├── 2019-05-29-hello-world.md
│   └── 2020-05-30-welcome.md
├── docs
│   ├── doc1.md
│   ├── doc2.md
│   ├── doc3.md
│   └── mdx.md
├── src
│   ├── css
│   │   └── custom.css
│   └── pages
│       ├── styles.module.css
│       └── index.js
├── static
│   └── img
├── docusaurus.config.js
├── package.json
├── README.md
├── sidebars.js
└── yarn.lock
```

for most of us,we just change `doucusaurus.config.js` file & save `.md` to `/blog`& `/docs` fold.

#### image style

in typora/vscode or other apps, u can use `<img src="" style="zoom:50%" />` to set img style,but cant in react/docusaurus.

- u can use this, but not work in `typora` & cause `docusaurus-plugin-image-zoom` plugin not working in docusaurus.

    ```html
    <img src="" alt="" style={{ zoom: '0.5' }} />
    ```

- **prefer** (this can be used in all `docusaurus & typora & vscode`)
  
  ```html
  <img src="" alt="" width="70%" />
  ```

#### image zoom preview

> refer to [docusaurus-plugin-image-zoom](https://github.com/gabrielcsapo/docusaurus-plugin-image-zoom)

```js
zoom: {
  // u should Comment this line
  // selector: ".markdown > img",
  background: {
    light: "rgb(255, 255, 255,0.8)",
    dark: "rgb(50, 50, 50,0.8)",
  },
},
```

#### Change Font

> refer to [docs](https://docusaurus.io/docs/static-assets) & [recursive](https://github.com/arrowtype/recursive)

- new fold named `font` in `/static/`
- download your fonts to it
- add to `/src/css/custom.css`

```css
@font-face {
  font-family: "RecMonoCasual";
  src: url("/font/RecursiveMonoCslSt-Regular.woff2") format("woff2-variations");
}
html {
  font-family: "RecMonoCasual";
}
h1,
h2,
h3,
h4,
h5,
h6 {
  font-family: "RecMonoCasual";
}
a,
p,
ul,
li,
ol,
blockquote,
div,
code,
table,
span {
  font-family: "RecMonoCasual";
  font-weight: 600 1000;
  /* if u want change font weight,set here,Otherwise, the original style of h1/h2...h6 will be changed  */
}
```

#### Table of content

> refer to [toc](https://docusaurus.io/docs/markdown-features/toc)

add to `docusaurus.config.js`

```js
  // By default, only shows h2 and h3 headings
    tableOfContents: {
      minHeadingLevel: 2,
      maxHeadingLevel: 6,
    },
```

## Cloudfare

if u need Cloudfare host your website, first create a repository in github & push blog fold to remote repo

- login to [cloudfare](https://dash.cloudflare.com/login)

- select pages table -> connect to git

- build settings
  - build command `npm run build`

  - out directory `/build`

      <img src="https://cdn.jsdelivr.net/gh/dev24hrs/blog-img/blog/202403262356240.png" alt="img"  width="70%"  />

Congratulations! pls visit your site.

## Picgo in Vscode

> refer to [picgo](https://picgo.github.io/PicGo-Doc/zh/guide/)
>
> if u forget your GitHub tokens, u cant find it in the blew file `data.json`

```json
// the data.json saved all the uploaded imgs info
// this is vscode settings
"picgo.dataPath": "$home/Library/Application Support/picgo/data.json",
```

<img src="https://cdn.jsdelivr.net/gh/dev24hrs/blog-img/blog/20240327151718.png"   alt="vscode" width="70%" />
