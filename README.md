
# Introduction

This is the repository for my academic website. Eventually, this README file will provide a place for me to record my process for getting my website up. I am a true amateur in this area, so I mostly based what I did on tutorials found around the Internet.

Currently, I use Netlify for deployment and Google Domains for registering the URL.

# Links

I used at least the following websites to set things up.

- https://github.com/wowchemy/starter-hugo-academic
  - This one is pretty obvious, but the website for wowchemy is a constant point of reference. This includes in dealing with the "failed to resolve output" error that I run into every now and then (requires clearing the cache or manually deleting, along with editing the config.yaml outputs, specifically commenting out the `home:` line)
- Will add to this list later
- Here are some that I used but need to add notes to later
  - https://github.com/jlperla/web-academic
  - https://isabella-b.com/blog/hugo-academic-customization/
  - https://www.kyleichan.com/post/hugo-academic/
  - https://www.emmanuelteitelbaum.com/post/create-a-website-with-blogdown-and-hugo/
- I also frequently have to consult the wowchemy documentation: https://wowchemy.com/docs/

# Random Notes

Some things to note, for later reference, when I come across errors

- Spent a while debugging an error `WARN... found no layout file for "HTML" for layout...` - turns out I just needed to clear my cache `hugo mod clean`.
- Many issues can be solved by just restarting my computer; always try that first before doing whatever is suggested by the error.
- When moving to a new computer, need to follow the instructions at this link to install dependencies, such as `golang`: https://wowchemy.com/docs/getting-started/install-hugo-extended/
- for using `git` via the command line, first use `brew` to install `git` and the credentials manager, then for each change commit the change with a label and finally push to origin. I also include the commands below to define my username and email address for a commit.
  - `brew install git`
  - `brew install --cask git-credential-manager`
  - `git commit -a -m "label here"`
  - `git push origin`
  - `git config --global user.name "My name"`
  - `git config --global user.email you@example.com`
- I ran into an error starting in March 2024 because the academic theme at that time didn't work with the newest version of `hugo`, these are the steps that I took to fix it
  - First I completed some steps that may have not been necessary, but I want to document
    - Followed the instructions from https://docs.hugoblox.com/reference/update/ to upgrade the modules I am using - following the breaking changes outlined for version 5.9 for Hugo Blox (the new name for these sets of themes), I changed my module from `module/wowchemy` to `module/wowchemy-bootstrap` in `go.mod`
    - I also added any new required modules listed in `go.mod` to `config/_default/config.yaml`
    - In `netlify.toml`, I initially changed the version of `hugo` to `0.123.8` which is the newest version; however, I discovered searching online that only up to `0.122.0` is supported
  - I then downgraded to a previous version of `hugo`, which seemed to be the step that was really necessary
    - I then followed instructions to find the formula (`hugo.rb`) in the `homebrew-core` GitHub page, look through history to find version `0.122.0`, download the raw file, and then save locally; after uninstalling (`brew uninstall hugo`), I then changed directories to where the previous version of `hugo` was saved and installed it (`brew install hugo.rb`); finally, I pinned this version (`brew pin hugo`) so that it won't automatically update
- I am running into an error June 2024 because a reference to a page I know exists (/publication/egy-consp) is not being found when referenced in /project/west-and-consp/index.md. I found out what the issue was - I had been editing the egy-consp index file the previous day, and I put an error into it. Then, even after fixing the error, it didn't put the link back in the sitemap. Deleting everything in public and then running `hugo` fixed the issue.
- Some notes to remind myself where the different files are for different parts of the website (it can be difficult to keep track of these):
  - All publications, project pages, and courses are subdirectories in `content`
  - `content/_index.md` is where you'll find office location, hours, contact info, etc - everything at the bottom of my main page
  - `content/authors/admin/_index.md` is where you can change name, position title, university, various links and icons for social media etc, and biography - additionally, the image in that same folder `avatar.jpg` is where you can set the main picture for your profile
  - `static/uploads` is where you can put files that you want to link elsewhere on your website - for me, that is my CV and, occasionally, files related to a particular publication that I need provided in an alternative location
  - `config/_default/config.yaml` define here the base URL for the website, for the most part won't edit this
  - `config/_default/menus.yaml` is where you define what is on your main menu - either separate pages (e.g. `courses/`) or portions of your homepage (e.g. `#featured`)
  - `config/_default/params.yaml` is the location for defining theme, font, google analytics ID, the footer, and some other things that I generally don't need to edit 
