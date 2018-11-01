---
title: Documentation
id: version-0.81.0-documentation_index
original_id: documentation_index
---

The user documentation is located at [https://www.home-assistant.io](https://www.home-assistant.io). This section here is the place where we provide documentation and additional details about creating or modifying content.

The [home-assistant.io](https://home-assistant.io) website is built using [Jekyll](http://github.com/mojombo/jekyll) and [these dependencies](https://pages.github.com/versions/). The pages are written in [Markdown](http://daringfireball.net/projects/markdown/). To add a page, you don't need to know HTML.

You can use the "**Edit this page on GitHub**" link to edit pages without creating a fork. Keep in mind that you can't upload images while working this way. You work on your change and propose it via a Pull Request (PR).

Once you've created a Pull Request (PR), you can see a preview of the proposed changes by clicking *Details* against Netlify checker in the checkers section of the PR as soon as deployment is complete.

For larger changes, we suggest that you clone the website repository. This way, you can review your changes locally. The process of working on the website is no different from working on Home Assistant itself.

To test your changes locally, you need to install **Ruby** and its dependencies (gems):

- [Install Ruby](https://www.ruby-lang.org/en/documentation/installation/) if you don't have it already. Ruby version 2.3.0 or higher is required.
- Install `bundler`, a dependency manager for Ruby: `$ gem install bundler`
- In your home-assistant.io root directory, run `$ bundle` to install the gems you need.

Shortcut for Fedora: `$ sudo dnf -y install gcc-c++ ruby ruby-devel rubygem-bundler rubygem-json && bundle`
Shortcut for Debian/Ubuntu: `$ sudo apt-get install ruby ruby-dev ruby-bundler ruby-json && bundle`

Then you can work on the documentation:

- Fork home-assistant.io [git repository](https://github.com/home-assistant/home-assistant.io).
- Create/edit/update a page. The components/platforms documentation is located in `source/_components/`. `source/_docs/` contains the Home Assistant documentation itself. 
- Test your changes to home-assistant.io locally: run `bundle exec rake preview` and navigate to [http://127.0.0.1:4000](http://127.0.0.1:4000)
- Create a Pull Request (PR) against the **next** branch of home-assistant.io if your documentation is a new feature, platform, or component.
- Create a Pull Request (PR) against the **current** branch of home-assistant.io if you fix stuff, create Cookbook entries, or expand existing documentation.

It could be necessary that you run `bundle exec rake generate` prior to `bundle exec rake preview` for the very first preview.

Site generated by `bundle exec rake` is only available locally. If you are developing on a headless machine, use port forwarding:

```bash
$ ssh -L 4000:localhost:4000 user_on_headless_machine@ip_of_headless_machine
```
## Speeding up site generation

Every release we post long changelogs to the website. This slows down generation of the website significantly! We include some tools to temporarily exclude components and blog posts that you're not working on out of the way.

```bash
bundle exec rake isolate[filename-of-blogpost-or-component]
```

When you're done working on the site, run the following command to move the pages back again:

```bash
bundle exec rake integrate
```