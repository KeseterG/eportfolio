+++
title="E-Portfolio"
description="Yes, this might be surprising - this website is also one of the projects I made. This e-portfolio uses Static-Site Generator (SSG) Zola for content generation, and Pico.css as the base framework of visual presentation. It is designed to have most of the content written and rendered in the form of markdown, without too much raw html."
date="2023-11-09"

[taxonomies]
categories=["Project"]
skills=["Web Development", "Design"]

[extra]
byline = "Fully Markdown-Based, Aesthetically Appealing Static Website"
timeframe = "October 2023 - Now"
organization = "Personal Project"
code_link="https://github.com/KeseterG/eportfolio"
title_image="images/ep-sqr.png"
+++

## Principle of Design

During the initial phase of the website, I set several core principles that I think matter the most.
Those principles guide the design, development, and future maintenance of the website.

1. **Markdown**. Markdown is one of my favorite ways to write content. The symbol is enough for me to create anything I want, and it can be even expanded with plugins and other templates (this will be expanded in the template section). Most importantly, when I'm done writing all the pages, I want to just focus on **content** - writing markdown is much easier to maintain, has a higher level of modularity, and is much more elegant. So, one of the most important things for me is to have **everything in markdown**.
2. **Static**. This is more of a realistic consideration. The most important audience is - of course - HR looking at my portfolio. I want them to access the information as fast as possible. I also don't want to bother to host a new server and a domain, static websites are much more convenient, as they can be held easily under GitHub pages.
3. **Appealing**. I like nice fonts, color combinations, and layouts. I want my website to look beautiful not only to showcase but also to satisfy myself. This is a simple but important reason.

With such requirements, I finally chose to use [Zola](https://www.getzola.org/) and [Pico.css](https://picocss.com/) as the main tech stack I'm going to use.

*Zola* is a static site generator (SSG) written in Rust Programming Language. It is super-fast and supports [Tera](https://github.com/Keats/tera), a template engine similar to Jinja2 and Django Template Language (which I'm familiar with).

*Pico.css* is a minified CSS framework. I used it very often for my projects, and that's the reason it became my top choice. It reaches a good balance between functionality and file size.

## Aestheics

During the early phase of development, I set the fonts, theme colors, and layout of the website.

Most of the decisions are based on my personal preferences. I like cold colors with sharp angles, combined with sans-serif fonts. These things led to the final visual outlook of the website.

The website uses [Nord](https://www.nordtheme.com/docs) theme for a sense of technology. The main font for this site is *Inter*, and the complementary font for emphasizing contents is *Montserrat*. Both of them are sans-serif and are widely used as web fonts.

## Editing

With all the previous things done, I can finally focus on creating the content.

{{ image(name="images/editing.png", alt="Editing Window")}}
{{ caption(caption="Editing in VSCode.") }}

Nearly all the editing can be done in VSCode, with the support of plugins and fast SSG. After the content is written, publishing is also easy - it's just about the use of Git. I also did many things to accelerate my editing. Custom VS Code snippets and Zola Shortcodes allow me to have more complex functions inside the markdown, beyond what normal markdown can do. For example, the caption and quad images utilize shortcodes that can be directly used in markdown.

{{ quad(name1="images/buzz.png", alt1="buzz",name2="images/buzz.png", alt2="buzz",name3="images/buzz.png", alt3="buzz",name4="images/buzz.png", alt4="buzz") }}

{{ caption(caption="The Four Buzzes are Laied out using the Quad Shortcode!") }}
