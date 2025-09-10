# Template for Encrypted Single Page Website

This encrypted site based on template here https://a-nau.github.io/password-protected-website-template



# How to Make DeMille Internal Resources Page
How to generate the encrypted DeMille Lab Internal Resources Page on Github Pages. This procedure works on MacOS, maybe one day I'll try to do it on Windows.

---

## 1. If starting from scratch: Fork the Template Repository
- Original repo: [https://github.com/a-nau/password-protected-website-template](https://github.com/a-nau/password-protected-website-template)  
Otherwise use the git repo for our internal resources page which is on the demillegroup github (github.com/demillegroup/internal-resources) and is helpfully called "internal-resources"

---
## 2. Create/edit main.html
This is the internal resources page.
Here is an example
```
<!DOCTYPE html>html
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>DeMille Internal Resources Links</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      margin: 2rem;
      background-color: #f9f9f9;
    }
    h1 {
      color: #333;
    }
    ul {
      list-style-type: none;
      padding: 0;
    }
    li {
      margin-bottom: 0.75rem;
    }
    a {
      color: #0066cc;
      text-decoration: none;
    }
    a:hover {
      text-decoration: underline;
    }
  </style>
</head>
<body>
  <h1>DeMille Internal Resources Links</h1>
  <ul>
    <li><a href="https://www.youtube.com/watch?v=dQw4w9WgXcQ&list=RDdQw4w9WgXcQ&start_radio=1" target="_blank">Click on me!</a>A description of what this link is...</li>
```

You should put main.html in the internal-resources folder on your local machine
**NOTE: The whole point of locally encrypting is that we don't have the unencrypted internal resources page on github, so don't push the unencrypted main.html to the repo or else you'll have to go edit the repo history.*

When you encrypt this file (by following the rest of the steps in this document) you'll end up with `internal-resources/encrypted/main.html`. This needs to become index.html. Is this a clunky way to do things? Yes but I already forked the template repo which wants this structure and it takes one line in terminal to rename and move the encrypted main.html into the right place.
## 3. Install StatiCrypt

[Staticrypt](https://github.com/robinmoisson/staticrypt)
This is easiest to do if you have node installed (which is easiest to do if you have homebrew)
```bash
brew install node
```
Then you can install staticrypt:
```bash
npm install -g staticrypt
```

This provides the `staticrypt` command for local encryption.

---

## 4. Encrypt `main.html` Locally

```bash
staticrypt main.html -p YOUR_PASSWORD --short --template "password_template.html"
```

- `YOUR_PASSWORD`: your password
- Generates `./encrypted/main.html`
---

## 5. Remove `main.html` from the repository and create index.html

- Stop tracking (this may already be done in which case you'll see "'main.html' did not match any files")

```bash
git rm --cached main.html
```
- Make index.html
```bash
mv ./encrypted/main.html index.html
```
- Push index.html
```
git add index.html
```
etc. etc.
