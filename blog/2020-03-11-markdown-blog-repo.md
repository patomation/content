---
templateKey: blog-post
title: Markdown Blog Repo
date: 2020--17T15:04:10.000Z
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
