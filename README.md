# The Gizmolab website

## This website was made using Hugo and Netlify CMS

## How to use the website:

#### Connect to the Admin panel:
  - Visit `https://gizmolab.netlify.app/admin`
  - Log in with the Teams' github credentials.

#### Make a new post:
  - Select the correct category from the left menu.
  - Add a Title, Keywords and Body
  - Slug: 
    - Slug is the string of characters at the end of a URL
    `https://random-website.com/posts/this-is-a-slug`
    - If the Title of the post is: "Why Vim is a great text editor", an example of a fitting slug is "why-vim-is-a-great-text-editor"

## How to develop the website

#### Requirements:

Download the latest versions of:
  - `git` [(install guide)](https://git-scm.com/downloads)
  - `hugo` [(install guide)](https://gohugo.io/getting-started/installing)
  - `npm` [(install guide)](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
  - After installing `npm`, install `netlify-cms-proxy-server`
  ```
  npm i -g netlify-cms-proxy-server 
  ```
  
Clone the repository

```
git clone https://github.com/g1zmolab/website
```

#### About `netlify-cms-proxy-server`

To use it, run the following command in the root of your project (the directory were this `README.md` is located).

```
npx netlify-cms-proxy-server
```

Now you can go ahead and edit the files.

You can find a lot of useful information in the Hugo and Netlify CMS documentation.
  - [Hugo docs](https://gohugo.io/documentation/)
  - [Netlify CMS docs](https://www.netlifycms.org/docs/intro/)


 
