---
layout: post
title:  "Customizing your github page."
date:   2021-10-28 12:00:00 +0200
---

![welcome](images/2021/customizing-your-github-page/welcome.png)

Github provides you great feature, as customization of your personal page, using markdown document and special type of GitHub repository. Let’s take a look on my personal GitHub page, for example.

![my customized page](images/2021/customizing-your-github-page/customized.png)

Look at that subtle blocks coloring. The tasteful thickness of them. Oh my God, it even has links...

I like this feature, because everyone who enter this page can get in with my personality, my tech stack and another information I could add to make people know something about me. There is only one way to create such stylish and sexy page. Let’s take a look how to implement it.

## Creating repository

Create repository, which name will match with your own GitHub nickname.

For example, my GitHub nickname is “Artefall”, so the repository will have the full name “Artefall/artefall”. Letter case is not essential.

![repo creation](images/2021/customizing-your-github-page/creating-repo.png)

## Update markdown file

Update markdown file with content, you want to be shown on your personal page.

Markdown is a simple language for formatting and stylizing your plain-text document. It’s easy to read markdown text, unlike HTML. Markdown doesn’t need any tags, instead markdown processor is required, because processor takes markdown and translate it to HTML format, therefore browser/another application, that supports markdown format can render it without any problem.

You can learn more about markdown here:

- https://www.markdownguide.org/getting-started/
- https://www.markdownguide.org/cheat-sheet/
- https://github.com/adam-p/markdown-here/wiki/-Markdown-Cheatsheet

I use markdown mostly in my GitHub for providing fancy-looking documentation or annotation in my repositories.

Afterall, create a commit to your repository.

Have you done it? That’s great! You can see now content of your markdown file on your personal GitHub page!
Extra step. Shields

Let’s consider how to implement blocks in markdown, also called “shields”. This blocks, maybe, are the best way to create really stylish GitHub home page. Shields look like this:

![shields](images/2021/customizing-your-github-page/shields.png)

To create such blocks, you need to use services shields.io, which internally uses simpleicons.org. You can find shields for any situation you can imagine! Download, statistics, information picture? You are welcome!

Also, simpleicons.org contains icons of every software, service,brand logos. I have personally checked it.

To make this block appear on your page, just past in your markdown file string, that will match the following pattern:

```
![<alt_name>](https://img.shields.io/badge/<string_that_will_be_shown_inside_block>-<block color: RGB HEX/color name>?logo=<icon_name_from_simpleicons.org>&logoColor=<logo_color: RGB HEX/color name>&style=<shield_style_from_shields.io>)
```

For example, I use this string to paste terraform shield.

![Terraform](https://img.shields.io/badge/terraform-7B42BC?logo=terraform&logoColor=white&style=for-the-badge)

Or this linkedin block, if you want to redirect on specific URL by clicking on shield:

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?logo=linkedin&logoColor=white&style=for-the-badge)](https://www.linkedin.com/in/artyom-maximov/)

Implementation:

```
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?logo=linkedin&logoColor=white&style=for-the-badge)](https://www.linkedin.com/in/artyom-maximov/)
```

shields.io service provides you even more options for customizing your blocks, so, check it out!

If you want to find out name of brand logo you need, got to simpleicons.org, pass brand name to search bar. Let’s search for terraform as for an example:

![search terraform](images/2021/customizing-your-github-page/icons.png)

Just take the exact name and RGB HEX code and pass it to corresponding pattern placeholders.
Congratulations!

{% include farewell.md conclusion="You have created a fancy-looking GitHub profile page!" %}