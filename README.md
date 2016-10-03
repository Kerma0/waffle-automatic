# Waffle-Test
[![Stories in Ready](https://badge.waffle.io/Kerma0/waffle-automatic.svg?label=ready&title=Ready)](http://waffle.io/Kerma0/waffle-automatic)

This is an empty repository to help setup __Waffle__ boards and use the __Automatic Work Tracking__.

## Setup the Waffle board

* Go to the [__Waffle__][1] home page and log in.
* Add your repository using the ![Add Project Button][2] button.
* Customize your board under __Project Settings__/__Columns__:
  - You can add/rename/delete columns depending on your needs.
  - You can define the columns on which the issues will be automatically moved by the __Automatic Work Tracking__.

![Columns Settings][3]

## Use the Automatic Work Tracking

Install the [__WaffleBot__][4] on your GitHub account.

#### Issues

When an issues is created, the card automatically goes under the __Backlog__ columns.

#### Branches

In order to solve this issue you must create a branch containing the id of the issue:
```
git checkout -b solve-issue#3
```
To be interpreted by the __WaffleBot__, the name of the branch must repect some rules:
* `3-solve-issue`: the name starts with the id of the issue, no '#'.
* `solve-issue#3`: the name doesn't starts with the id of the issue, the '#' is mendatory.
* `3-solve/issue`: the name is path-like and starts with the id of the issue, no '#'.
* `solve/#3-issue`: the name is path-like and doesn't starts with the id of the issue, it must be after the '/' with a '#'.

The id must be separated by a '-' or '_' with the rest of the name.

This will move the card in the column tagged with the __Work Started__ action (here the __In Progress__ column).

#### Pull Requests

When creating a new pull request in order to close an issue, the name or description of that pull request must contain a [GitHub closing Keywords][5]

If the pull request already exists, it is possible to connect issues to this one using the [Waffle connect Keywords][6] in the description of that pull request.

This will move the card in the column tagged with either the __New Collaborator PRs__ or __New Contributor PRs__ action (here the __Pending Validation__ column).

Finally merging the pull request will move the card in the __Done__ column.

[1]: https://waffle.io/
[2]: http://nsa38.casimages.com/img/2016/09/28/160928054757492263.png
[3]: http://nsa38.casimages.com/img/2016/09/28/160928053259714396.png
[4]: https://github.com/integration/wafflebot
[5]: https://help.github.com/articles/closing-issues-via-commit-messages/#keywords-for-closing-issues
[6]: https://github.com/waffleio/waffle.io/wiki/FAQs#prs-connect-keywords
