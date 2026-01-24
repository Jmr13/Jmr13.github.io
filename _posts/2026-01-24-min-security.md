---
layout: post
title:  "Min. Security"
date:   2026-01-24
---

## Dilemma
Before publishing the first entry of my blog, I was frantic at the thought that someone might hack it and change its content, despite its anonymity. Hosting a bare static website without any security measures in place may not be a good idea. Although setting [Nonce](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/nonce) in the security policy of HTML files prevents the execution of unwanted CSS styling and JavaScript code, you cannot stop a hacker from changing the text contents saved in a database (which I was not aware of before).

There are reports of security breaches that have happened even to the websites of small enterprises. Remembering those cases, my anxiety was amplified and justified. Even a low-traffic website with little to no visitors, like mine, can be a victim of such exploitation. My motivation to code vanilla HTML and CSS files, vanished.

I started researching all the possible SSG (Static Site Generator) available publicly. Coming from a React.js background, I initially considered using [Gatsby](https://www.gatsbyjs.com/), but I opted out after fully understanding the complexities behind the framework. Then, I stumbled upon [Jekyll](https://jekyllrb.com/), which is already fully integrated with [GitHub Pages](https://pages.github.com/). The hassle of deciding where to host this blog eased my mind.

Although the security concern still lingered, I reflected on the time when I didnt know how static site generators worked. I previously thought that the contents of the generated static files were being fetched from a database, then will be built dynamically.


## Comparison 
This is how I used to envision static site generators working:

![My assumption how SSG works](/assets/images/2026/01/24/ssg_flow_invalid.svg)

1. Content such as templates and text files are stored in a database.
2. The static site generator ingests all content to generate website files.
3. You pick a hosting service to serve all static website files.
4. Upon a user request, the static site generator runs to accommodate the web pages the user needs.

During the development of this blog and after reading the official Jekyll documentation, I realized how wrong I was. I had the [WordPress's](https://wordpress.com/) (A content Management System) mechanism in mind and assumed it was similar to SSG. After rereading a few articles, it became clear that I wouldn't be needing a database at all. SSGs are designed specifically to steer away from databases.

The diagram should now look like this:

![How SSG really works](/assets/images/2026/01/24/ssg_flow_valid.svg)

1. The static site generator builds the static web page files whenever the author updates the website content, even without any user requesting the pages from a browser (represented by the dashed lines connection to indicate a not on-demand request from the user)
2. The hosting platform (in this case, a CDN or it can be web server also) retrieves the static web page files and serves them.
3. Without database overhead, users can view the website immediately because the files were prepared ahead of time by the static site generators. 


## Wrap-up
That is how static site generators really work. Hackers have minimal ways to interrupt the flow and inject malicious scripts between user requests because a database is not involved. 

There is not much to worry about. SSGs have an upper hand in terms of security compared to well-known CMSs (Content Management Systems) like WordPress. They speed up content delivery, but a non-technical person should think twice before using them, as they require some coding.