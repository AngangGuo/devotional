+++
date = '2026-10-22T08:12:10-07:00'
draft = false
title = 'Project Setup'
+++

## Project Name
### Devotion vs Devotional
* Devotion is a noun that means deep love, loyalty, or commitment to a person, cause, or spiritual practice. In a spiritual context, it refers to the ongoing relational state of living for and drawing close to God.
* Devotional can function as an adjective or a noun:
    * As a noun, it is a book, booklet, or piece of literature (containing a Bible verse, a short reflection, and a prayer) used to guide spiritual thought. It can also refer to a short religious service.
    * As an adjective, it describes things related to worship or spiritual practice (e.g., "devotional reading" or "devotional music")

Example: Mornings With God: Daily Bible Devotional for Women: 365 Devotions to Inspire Your Day

## Devotional Project Setup
### Hugo Theme
Use submodule if you want to deploy the site to Netlify

```
hugo new site devotional
cd devotional
git init
git submodule add --depth 1 https://github.com/McShelby/hugo-theme-relearn.git themes/hugo-theme-relearn
```

Then add this at the top of your `hugo.toml`
```
theme = 'hugo-theme-relearn'
```

### Netlify Site
To host/deploy this project to the free Netlify site, do the following.

#### Configuration file
Add `netlify.toml` to your project root folder.
```
[build]
  command = "hugo"
  publish = "public"

[build.environment]
  HUGO_VERSION = "0.168.0"
```

#### Deploy
Sign in(Github) > Add new project > Select devotional repository from Github

Use the default configuration will deploy the site using a Netlify site name, e.g. splendid-raindrop-03e9c3.netlify.app

#### Customer Domain
To use a customer domain name `devotional.brideofchrist.ca`, set up according to the following steps.

Netlify > Project > Site configuration > Domain management
* Click `Add custom domain`
* Name: `devotional.brideofchrist.ca`
* Add verification code to your dns server

DNS Records(canspace.ca)
* CNAME: `devotional.brideofchrist.ca` -> `splendid-raindrop-03e9c3.netlify.app.`
* Add a verification record
    * Service: Other (paste the full value)
    * Verification value: `subdomain-owner-verification=1e2688xxx`

### Remove tracked files from Github
I commited the `public` folder by mistake, to remove all the files from Github

* Remove the file from Git tracking
```
// remove one file
git rm --cached path/to/file

// remove the public folder
git rm -r --cached public
```

* Add the folder to `.gitignore` file
* Commit and push changes

