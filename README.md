
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
