# www.opendisclosure.io

_This project is currently in MVP stage. We are currently working on getting
this project to feature parity with the existing
[opendisclosure.io][opendisclosure-io] website._

[Open Disclosure California][opendisclosure-io] provides transparent,
non-partisan campaign contribution and expenditure data in an accessible and
easy to understand format. We hope this site will engage the voting public and
raise awareness and accountability. Ultimately, this is one step toward shifting
politics into a movement of civic engagement and ultimate citizen action.


## Prerequisites

- [Ruby 2.3](https://www.ruby-lang.org/)
- [Bundler](https://bundler.io/) gem
- [Make](https://www.gnu.org/software/make/)

Optionally:

- [Node 8.9](https://nodejs.org/)


## Setup

    $ bundle install
    $ bundle exec jekyll serve


## Findings

This project started as an experiment. Here is what we learned:

- `ballots` should probably just be renamed `elections`.
- naming of the files is very important, it's how we reference relationships
  between entities. Best is to use the full path name which would be unique per
  entity.
- Info we attribute to candidates, like bio, occupation, website, etc, should
  those be frozen in time based at the time of election? For example, London
  Breed is now running for Mayor, so many of these attributes have changed since
  the last election. Would folks be interested in seeing snapshots of websites,
  at the time of a previous election? i.e. should past elections just be
  snapshots of the opendisclosure website?


## Finance disclosures

The process of downloading, converting, and calculating the reported financial
disclosures is handled by
[disclosure-backend-static][backend-static].
To get the finance data into this project, we use [gulp.js](https://gulpjs.com/)
to copy the files over and do some light transformations on them to get them
into a [Jekyll Collection](https://jekyllrb.com/docs/collections/).

We commit all the finance data to this repo so that you do not need to use the
gulp tasks to help with this project. _You only need to run the gulp tasks if you
want the latest finance data._

This process is optional and temporary. It allows us to update the finance data
while allowing local modifications and overrides. If you have thoughts on how
this could be improved, [let us
know](https://github.com/adborden/odca-jekyll/issues/5)!


### Update the finance data

In order to get the latest finance data, first clone
[disclosure-backend-static][backend-static] as a sibling to this project's
directory. _It is important that the `disclosure-backend-static` project is
cloned to the correct path (`../disclosure-backend-static`) which is hardcoded
in the gulpfile (pull requests welcome)._

Next, follow the instructions in
[disclosure-backend-static](https://github.com/caciviclab/disclosure-backend-static/blob/master/README.md)
and run a build. Then you can run the npm task:

    $ npm run pull

This will copy over all files as-is and will overwrite any local modifications.
It's important to review the changes before committing them so as not to lose
any intentional changes.


[backend-static]: https://github.com/caciviclab/disclosure-backend-static
[opendisclosure-io]: http://www.opendisclosure.io/
