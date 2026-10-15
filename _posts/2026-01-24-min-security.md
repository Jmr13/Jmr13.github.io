---
layout: post
title:  "Min. Security"
date:   2026-01-24
---

## Dilemma
Before publishing the first entry of my blog, I was frantic at the thought that someone might hack it and change its content, despite its anonymity. Hosting a bare static website without any security measures in place may not be a good idea. Although setting [Nonce](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/nonce) in the security policy of HTML files prevents the execution of unwanted CSS styling and JavaScript code, you cannot stop a hacker from changing the text contents saved in a database (which I was not aware of before).

There are reports of security breaches that have happened even to the websites of small enterprises. Remembering those cases, my anxiety was amplified and justified. Even a low-traffic website with little to no visitors, like mine, can be a victim of such exploitation. security threats don't always discriminate based on popularity. A website is compromised simply because it presents an opportunity. My motivation to code vanilla HTML and CSS files, vanished.

I started researching all the possible SSG (Static Site Generator) available publicly. Coming from a React.js background, I initially considered using [Gatsby](https://www.gatsbyjs.com/), but I opted out after fully understanding the complexities behind the framework. Then, I stumbled upon [Jekyll](https://jekyllrb.com/), which is already fully integrated with [GitHub Pages](https://pages.github.com/). The hassle of deciding where to host this blog eased my mind.

Although the security concern still lingered, I reflected on the time when I didnt know how static site generators worked. I previously thought that the contents of the generated static files were being fetched from a database, then will be built dynamically.

In hindsight, I had been approaching the problem with the wrong mental model. I was imagining a website that constantly needed to retrieve and assemble its content, when the whole point of static site generation is to prepare much of that work in advance.

## Comparison 
This is how I used to envision static site generators working:

![My assumption how SSG works](/assets/images/2026/01/24/ssg_flow_invalid.svg)

1. Content such as templates and text files are stored in a database.
2. The static site generator ingests all content to generate website files.
3. You pick a hosting service to serve all static files.
4. Upon a user request, the static site generator runs to accommodate the web pages the user needs.

During the development of this blog and after reading the official Jekyll documentation, I realized how wrong I was. I had the [WordPress's](https://wordpress.com/) (A content Management System) mechanism in mind and assumed it was similar to SSG. After revisiting a few articles and examining the process more carefully, I realized that I didn't need a database at all for my intended setup. SSGs are designed specifically to steer away from databases. Unlike a traditional database-driven website, a static site generator can build the entire website from files stored locally or in a repository, without querying a database every time a visitor requests a page.

The diagram should now look like this:

![How SSG really works](/assets/images/2026/01/24/ssg_flow_valid.svg)

1. The static site generator builds the static web page files whenever the author updates the website content, even without any user requesting the pages from a browser (represented by the dashed lines connection to indicate a not on-demand request from the user)
2. The hosting platform (in this case, a CDN or it can be web server also) retrieves the static web page files and serves them.
3. Without database overhead, users can view the website immediately because the files were prepared ahead of time by the static site generators. 

The distinction is subtle but important. A static site generator does its work primarily during the build process, while a conventional dynamic website may perform some of that work whenever a visitor requests a page. Of course, static sites can still integrate external APIs, databases, and other dynamic services, but those features are not required for a basic blog.

## Wrap-up

That is how static site generators work in a typical setup. Without a database or server-side application handling every page request, a basic static website has a smaller attack surface than many traditional dynamic websites. There are fewer moving parts to maintain and fewer opportunities for certain types of attacks to occur during normal page delivery.

However, this doesn't mean static websites are invulnerable. An attacker could still compromise the repository, steal account credentials, tamper with the build pipeline, or exploit a vulnerable dependency. If that happens, malicious content could be introduced into the generated files before they are published. Security still matters, even when the website itself consists of nothing more than HTML, CSS, and JavaScript.

In the end, this little detour taught me something I hadn't expected to learn before publishing my first blog post. The best way to address a problem isn't to add more layers of protection, but to understand how the system works and choose an approach that reduces the risks from the very beginning.

