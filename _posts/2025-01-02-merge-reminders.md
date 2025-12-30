---
layout: post
date: 2025-01-02
title: Merge Reminders
description: Don't forget
image: https://github.com/pjflanagan/merge-reminders/raw/main/readme/comment.png?raw=true
github: https://github.com/pjflanagan/merge-reminders
website: https://github.com/marketplace/actions/merge-comment-reminders
---

I work solo on a lot of projects, meaning the only person to review my code is me.
Sometimes, when revisiting a project after a break, I forget exactly how to work on a project.
It can be helpful to leave comments behind, but those often get overlooked.

Now comments can become more powerful. By flagging a comment with `MERGE:` I can make
that comment appear automatically on a pull request. 

![Merge Comment Reminders PR Comment](https://github.com/pjflanagan/merge-reminders/blob/main/readme/comment.png?raw=true)

## Installation

First, add this code to `.github/workflows/merge-comment-reminders.yml`

{% highlight yml %}
name: Merge Comment Reminders

on:
  pull_request:
    types: [opened, edited, synchronize]

jobs:
  merge-comment-reminders-action:
    runs-on: ubuntu-latest

    steps:
      - name: Merge Comment Reminders
        uses: pjflanagan/merge-reminders@v1.0.0
{% endhighlight %}

Make sure you have enabled read and write action permissions in you Github repository settings.
To do so, go to Actions > General > Workflow permissions and allow actions to "Read and write permissions"

## Usage

Add comments beginning with `MERGE:` to your code like this:

{% highlight tsx %}
// Header.tsx

const offsetHeight = 120; // MERGE: Be sure `offsetHeight` is reflected in `style.module.scss`
{% endhighlight %}

Comments can use Markdown and Github usernames:

{% highlight python %}
# api.py

# MERGE: Update the [documentation](https://docs.example.com) or @pjflanagan will be **very** upset
class API:
  # ...
{% endhighlight %}

Then, when a dev creates a PR that modifies a file with `MERGE:` comments,
those instructions will automatically be commented on your PRs. Like this:

```
**Merge Reminders**
- [ ] `Header.tsx`: Be sure `offsetHeight` is reflected in `style.module.scss`
- [ ] `api.py` Update the [documentation](https://docs.example.com) or @pjflanagan will be **very** upset
```

You can then enforce all PR checkboxes are ticked before merging using [Task Completed Checker](https://github.com/marketplace/actions/task-completed-checker).

Now you've configured your repo to require devs to acknowledge instructions for each file they updated. This is useful when:
- You want to ask devs to adhere to a pattern
- You need devs to update a different file to match changes in this one
- You need to remind devs to update documentation
- You need devs to be aware of how their code changes might cause unwanted side effects

### Specific use cases

Merge Reminders only supports `#` and `//` comments. If the language uses a different type of comment
you'll have to fake it.

{% highlight html %}
<!--
  HTML comment
  # MERGE: be sure to update footer links to match the header links
-->
{% endhighlight %}
