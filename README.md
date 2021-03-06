git\_pivotal\_tracker_x
===========

Forked from the awesome Git Pivotal Tracker gem by Ben Lindsey and Carbon Five.  (You can find the original [here](https://github.com/blindsey/git_pivotal_tracker))

Changes included in this version:

* Option to automatically delete story branches once they've been merged
* Ability to pick your integration branch on the fly (when you start a new story)
* Changed git hook from prepare-commit-msg to commit-msg since commit-msg is better supported by git apps
  * I recommend [Brotherbard's GitX](https://github.com/downloads/phuibonhoa/git_pivotal_tracker/GitX.app.zip) (This is a slightly older version, because the newest one has performance issues for me).

Features
--------

* `git-story`
* `git-feature`
* `git-bug`
* `git-chore`

These commands start the first available story from your Pivotal Tracker project and create a topic branch for it.

* `git-finish`

When on a topic branch, this command will:

* Fetch the latest integration branch ('master' by default), 
* Rebase your topic branch from it
* Merge the topic branch into the integration branch with no-fast-forward 
* Push the integration branch to origin
* (Optionally) delete the topic branch

You can customize your integration branch in 2 ways.  You can set the integration branch in your git config (see config options below).  Additionally, when you create a topic branch, it prompts you for a branch suffix name; if the suffix name you supply is the name of an existing local branch, that branch will be used as your integration branch for that story only.  This method will override the integration branch specified in your git config when applicable.

* `git-info`

Print out the Pivotal Tracker story information for the current topic branch

Examples
--------

* FIXME (code sample of usage)

Requirements
------------

* a github account
* a Pivotal Tracker project
* Pivotal Tracker api service hook turned on for your github project (under Admin -> Service Hooks)

Install
-------

``gem install git_pivotal_tracker_x``

Once installed, git pivotal needs two bits of info: your Pivotal Tracker API Token and your Pivotal Tracker project id:

``git config --global pivotal.api-token 123a456b``

The project id is best placed within your project's git config:

``git config -f .git/config pivotal.project-id 88888``

If your project's access is setup to use HTTPS:

``git config -f .git/config pivotal.use-ssl 1``

If you prefer to merge back to a branch other than master when you've finished a story, you can configure that:

``git config -f .git/config pivotal.integration-branch develop``

If you prefer to fetch and rebase from origin before merging (default is no):

``git config --global pivotal.rebase 1``

If you prefer to fast-forward your merges into the integration branch (default is --no-ff):

``git config --global pivotal.fast-forward 1``

If your Pivotal Tracker user name is different than your git user name:

``git config --global pivotal.full-name 'Ben Lindsey'``

If you prefer to have story branches deleted after they are merged by `git-finish`:

``git config --global pivotal.delete-branch 1``

If you would like verbose logging turned on for git commands:

``git config --global pivotal.verbose 1``


Contributors
------
* [Philippe Huibonhoa](https://github.com/phuibonhoa/)
* [Ben Lindsey](https://github.com/blindsey)
* [Liron Yahdav](https://github.com/lyahdav)

License
-------

(The MIT License)

Copyright (c) 2011 Ben Lindsey

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
