---
title: "Moved my API doc site into separate repo"
categories:
- api-doc
keywords:
summary: "I recently moved my API doc course into a separate path. Previously, I had the material inside my main site in its own collection. But I wanted to completely separate out the site into its own repo, with its own theme and configuration file. This will allow me to more easily output the content to other formats, such as MOBI and PDF. I'm happy that I did this, as I think it allows users to focus more fully on the content."
bitlink: http://bit.ly/
---

If you click the **API Doc** button on my primary navigation bar, it takes you here: [idratherbewriting.com/learnapidoc/](http://idratherbewriting.com/learnapidoc/). Previously, there wasn't a separating path called "learnapidoc."

This doesn't seem like much of a change, but behind the scenes there is quite a bit that's different. First, I moved all the API doc content into its own repo here: [learnapidoc](https://github.com/tomjohnson1492/learnapidoc). (My blog's repo is [here](https://github.com/tomjohnson1492/tomjohnson1492.github.io).)

Additionally, I used a different theme with the content. I actually developed this theme for a [project at work](https://github.com/amzn/appstore-alexa-docs/) (which we open sourced), but it doesn't look like we'll be using the theme after all.

This theme includes a search and a multilevel menu that doesn't use an accordion toggle like my [previous doc theme](http://idratherbewriting.com/documentation-theme-jekyll/). I also added a breadcrumb that helps orient users. In the breadcrumb, "Home" takes you back to my blog.

I'm still fine-tuning the material. For example, I plan to add numbers back into the headers and provide next/previous buttons between each of the pages. However, for the time being, I haven't included these features. Hard-coding numbers into the titles is a serious pain if you decide to switch around topics or insert new ones. I need to do this programmatically if I do it at all.

One neat thing about using Github is that your repos are accessible from your home domain. In my main repo, [tomjohnson1492.github.io](https://github.com/tomjohnson1492/tomjohnson1492.github.io), I have a CNAME that redirects tomjohnson1492.github.io to idratherbewriting.com. When you add additional repos to your GitHub account, like learnapidoc, you can access the repo's content by going to tomjohnson1492.github.io/learnapidoc, but since your CNAME already redirects tomjohnson1492.github.io to idratherbewriting.com, it does the same for the other repos. Now you access learnapidoc by going to [http://idratherbewriting.com/learnapidoc].

In moving the URLs, I used the [Jekyll redirect from](https://github.com/jekyll/jekyll-redirect-from) plugin (which GitHub supports to create 301 redirects. I also used the [URL Mapper function from Disqus](https://help.disqus.com/customer/portal/articles/912757-url-mapper) to move my comment threads (though for some reason the comments on the homepage didn't move yet).

Why did I move the content? Well, I haven't even discussed this yet, but I've coded all the necessary files to output the content from this repo into MOBI output for Kindle. I want to publish this content as an e-book, among other things.

I initially experimented with [Gitbook](https://www.gitbook.com/@tomjohnson1492/dashboard) for its EPUB output, but in my experiments, the EPUB output kind of sucks on Kindle. Some navigation controls are missing, formatting is a bit messed up, and overall I don't like the loss of control. Plus, since I work for Amazon (but not in the Kindle division), I'd like to try generating my ebook using [Kindlegen](https://www.amazon.com/gp/feature.html?docId=1000765211). I'm still fine tuning things here, so stay tuned for more updates to come.

I also plan to incorporate PDF generation from the site (using [Prince XML](https://www.princexml.com/)), but I haven't gotten around to that yet. In the end, I want to output the content as HTML, MOBI (Kindle), EPUB, and PDF.

My kids tell me no one will buy the e-book if they can get the information online for free, so I've been thinking of using [Memberful](https://memberful.com/) to gate the web content with a paywall. However, I have mixed feelings about this for a number of reasons. Primarily, gated content isn't discoverable, so I'd lose a lot of readers right off the bat.

Second, sites with paywalls are usually delivered over HTTPS (for security), but GitHub Pages only supports HTTPS [if you don't use a CNAME](https://github.com/blog/2186-https-for-github-pages). (Remember, I use a CNAME to redirect tomjohnson1492.github.io to idratherbewriting.com.) Even with just HTTP, though, I doubt my site would be subject to hacking attempts given that it's entirely static (unlike database-driven CMS sites).

I probably make more off one advertiser than I would from any potential e-book sales. The traffic boost from the content is key for persuading advertisers to the site. (That said, this API doc site now exists as a separate site with its own theme that lacks the sidebar + banner ads, as do my other non-blog subsites in other repos.)

I'm still fine-tuning the content. Technology evolves daily, it seems, so things gradually slide out of date. It'll be at least another month of editing before I'm ready to kindle-ize it. I might experiment with different models, so we'll see.

Overall, I like the idea of putting effort into content that will eventually be published as a book. Blogging is fun and all, but after posts slide off the homepage, they're yesterday's news. A blog post is extremely short-lived. After a few years, most people assume the content is out of date.

Instead of pouring so much energy into long-form blog posts, I'd like to pour that effort into pages that will eventually form into a book. The pages will also be published online, so it probably won't make that much of a difference.

I think I'll start treating blog posts more like their original intent: web logs, or journals. A blog should chronicle your daily thoughts and efforts. I find that these kind of entries are more engaging anyway. Most of us already have the knowledge we need. But we read because wee enjoy hearing another's voice, following the person's thoughts and activities as they try to achieve this or that goal.

People always tell me that they've "been following my blog for years." When I hear this, I'm always surprised, because they've usually never made a comment or even read my latest posts that week. But there's something about following someone online that's different from reading a book author. To be a blogger really means to be a "web logger," a journal writer, and people often connect with that content more intimately than they do content from a book.

I myself frequently look for tidbits to read online. When I need a break, or want to unwind, or just get a little bored, I'd like to read a good blog post. I don't want to read something thick, drenched with all kinds of research or how-to or other information. I just want to read 500-1000 words of someone's thoughts, speaking to me in a unique way. Something light but interesting. Something to make me smile before I return to the grind of whatever I'm documenting.