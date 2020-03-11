---
templateKey: blog-post
title: Markdown Blog Repo
date: 2020-03-11T15:04:10.000Z
featuredpost: false
featuredimage: /img/flavor_wheel.jpg
description:
tags:
  - markdown
  - gatsby
  - git
  - repo
  - netlify
  - build hooks
---

I have been using markdown for writing blogs for blogs and templates for a while. First I used WordPress. Then I started using github pages which is ruby based. Then since I got really into react I thought I would try my hand at using Gatsby to generate static sites.

Both of theses later methods don't use a database to store the content they use markdown.
This is nice not having to have a database because you can see all your content as text files and down have to migrate databases or worry about corruption.
The only thing I don't care for is the commits for these blog files gets mixed in with the development commits for my styles and html and other things.
I feel like this is a bit messy when I'm trying to keep better standards for commit messages and what not.

Throw that in with a cms tool like netlify or forestry and you get commit messages for every time you save something. It would be nice to keep all those commits in a separate place not included with my code commit changes.
Additionally, I don't enjoy writing when I'm looking at the huge file tree that Gatsby needs to run itself. Sure I can keep all my markdown in a pages or a pages/blog folder but I find that problematic.

I would also like to continually save without having to write a commit message for each save. This could create a bunch of commits that would make it more difficult for me to view the code history for making style and theme changes.

This brings me to the next phase where I want a repo for the markdown content and a repo for the gatsby code.
But how can I make this work and still be able to use the netlify cms if I want to. So far I haven't made use of this.

I will now walk through my process of researching possible solutions.

### Requirements
- Still be able to use netlify cms
- Saving on the blog repo triggers a build with netlify build hooks
- Blogs need to me marked as draft until ready and not published.

I found a plugin for gatsby that looks promising. Its called ```gatsby-source-git```

Add this to your plugin gatsby config
```
{
  resolve: `gatsby-source-git`,
  options: {
    name: `content-repo`,
    remote: `https://github.com/patomation/content.git`,
    branch: `master`,
    patterns: `*`
  }
}
```

I'll have to explore the patterns option.
I see that you can include files in a folder or by extension.
I'm hoping to use a file structure like so:

- Repo
  - blog
  - projects
  - packages

I want to be able to write blogs every so often. I would also like to write content pages for each of my projects in my portfolio. Additionally I would like a place to keep the writings about npm packages I've published.

Lets see how that goes.
I've installed the plugin: ```npm install gatsby-source-git --save```
And I've added it to my config.

I started up the gatsby development server and one thing that breaks right off the bat is some of the markdown front matter stuff.
For instance the gatsby cms starter that I'm using is not finding the tags or the date front matter. So maybe I'm doing it wrong?

Now that I'm looking into this issue I'm finding that something else broke. Not sure how that happened. But it might have something to do with how I removed the markdown files. Maybe this depends on the files being there. So I'm going to put then back for a moment and try to figure out how to remove the files later.

That was what it was. When I removed the markdown files from the codebae repo we get these errors. I just need to figure out how I can run the site with no. Markdown files at all without it breaking. This also shows that It wasn't reading the markdown files from the 2nd repo correctly.

So the blogs are not showing up like I thought they would. But the readme for ```gatsby-source-git``` does go on to talk about how you can query for the files... So lets take a look at that.

I went to the graphql playground that gatsby serves up and tryed to query for the files from the repo with this. And no files are returned. This means, that I will have to look at how the files get imported in the config ```patterns``` section...

```
{
  allFile(filter: { sourceInstanceName: { eq: "content-repo" } }) {
    edges {
      node {
        extension
        dir
        modifiedTime
      }
    }
  }
}
```























//
