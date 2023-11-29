# The Gizmolab website

## This website was made using Hugo and Netlify CMS

## How to use the website:

#### Connect to the Admin panel

- Visit `https://gizmolab.netlify.app/admin`
- Log in with the Teams' github credentials.

#### Make a new post

- Select the correct category from the left menu.
- Add a Title, Keywords and Body
- Slug:
  - Slug is the string of characters at the end of a URL
  `https://random-website.com/posts/this-is-a-slug`
  - If the Title of the post is: "Why Vim is a great text editor", an example of a fitting slug is "why-vim-is-a-great-text-editor"

## How to develop the website

#### Requirements

Download the latest versions of:

- `git` [(install guide)](https://git-scm.com/downloads)
- `hugo` [(install guide)](https://gohugo.io/getting-started/installing)
- `npm` [(install guide)](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
- After installing `npm`, install `netlify-cms-proxy-server`

  ```bash
  npm i -g netlify-cms-proxy-server 
  ```
  
Clone the repository

```bash
git clone https://github.com/g1zmolab/website
```

#### About `netlify-cms-proxy-server`

To use it, run the following command in the root of your project (the directory were this `README.md` is located).

```bash
npx netlify-cms-proxy-server
```

Now you can go ahead and edit the files.

You can find a lot of useful information in the Hugo and Netlify CMS documentation.

- [Hugo docs](https://gohugo.io/documentation/)
- [Netlify CMS docs](https://www.netlifycms.org/docs/intro/)


# Custom changes

```diff
--- b/layouts/partials/head.html
+++ b/layouts/partials/head.html
@@ -28,6 +28,8 @@
   <link rel="stylesheet" href="{{ "style.scss" | absURL }}">
 {{- end }}

+<link rel="stylesheet" href="/css/custom.css">
+
 <!-- Icons -->
 {{ if isset $.Site.Params "favicon" }}
   <link rel="shortcut icon" href="{{ $.Site.Params.favicon | absURL }}">
@@ -48,15 +50,15 @@
 <!-- OG data -->
 <meta property="og:locale" content="{{ $.Site.Language.Lang }}" />
 <meta property="og:type" content="{{ if .IsPage }}article{{ else }}website{{ end }}" />
-<meta property="og:title" content="{{ if .IsHome }}{{ $.Site.Title }}{{ else }}{{ .Title }}{{ end }}">
+<meta property="og:title" content="{{ if .IsHome }}{{ $.Site.Title }}{{ else }}{{ .Title }} :: {{ $.Site.Title }}{{ end }}">
 <meta property="og:description" content="{{ if .IsHome }}{{ $.Site.Params.Subtitle }}{{ else if .Description}}{{ .Description | plainify }}{{ else }}{{ .Summary | plainify }}{{ end }}" />
 <meta property="og:url" content="{{ .Permalink }}" />
 <meta property="og:site_name" content="{{ $.Site.Title }}" />
-{{ if and (not .IsHome) (isset .Params "cover") }}
-  <meta property="og:image" content="{{ .Param "cover" | absURL }}">
+{{ if and (not .IsHome) (isset .Params "thumbnail") }}
+  <meta property="og:image" content="{{ .Params.thumbnail | absURL }}">
 {{ else }}
-  {{ if isset $.Site.Params "favicon" }}
-    <meta property="og:image" content="{{ $.Site.Params.favicon | absURL }}">
+  {{ if $.Site.Params.customCover }}
+    <meta property="og:image" content="{{ $.Site.Params.customCover | absURL }}">
   {{ else }}
     <meta property="og:image" content="{{ printf "img/favicon/%s.png" $.Site.Params.ThemeColor | absURL }}">
   {{ end }}
```

```diff
--- a/layouts/partials/footer.html
+++ b/layouts/partials/footer.html
@@ -7,7 +7,6 @@
       <div class="copyright">
         <span>© {{ now.Year }} Powered by <a href="http://gohugo.io">Hugo</a></span>
     {{ end }}
-        <span>:: Theme made by <a href="https://twitter.com/panr">panr</a></span>
       </div>
   </div>
 </footer>
```
