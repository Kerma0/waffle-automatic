# Waffle-Test

This is an empty repository to help setup __Waffle__ boards and use the __Automatic Work Tracking__.

## Setup the Waffle board

* Go to the [__Waffle home page__][1] and log in.
* Add your repository using the ![Add Project Button][2] button.
* Customize your board under __Project Settings/Columns__:
  - You can add/rename/delete columns depending on your needs.
  - You can define the columns on which the issues and pull requests will be moved by the __Automatic Work Tracking__ (by setting the actions __Work Started__, __New Contributor PRs__ and __New Collaborator PRs__ on the required columns).

![Columns Settings Example][3]

## Use the Automatic Work Tracking

Install the [__WaffleBot__][4] on your GitHub account.

#### Close Issues

When an issues is created, a card is automatically created in the __Backlog__ column.

There are 3 different ways to manage an issue:
* Commit using [GitHub closing Keywords][5] and the id of the issue (e.g: `git commit -m 'This closes #3'`):
  * This will move the card in the __Done__ column.
  * It's still possible to connect this issue to a pull request ([Connect Issues](#connect-issues)).
* Create a new pull request ([Create Pull Requests](#create-pull-requests)):
  * This will move the issue and pull request cards in the column(s) tagged by the __PRs__ actions.
  * It's still possible to connect issues to this pull request ([Connect Issues](#connect-issues)).
  * Closing the pull request will move both cards in the __Done__ column.
* Connect the issue to an existing pull request ([Connect Issues](#connect-issues))
  * This will move the issue card in the column(s) tagged by the __PRs__ actions.
  * Closing the pull request will move both card in either the __Done__ column as a merged card,<br>
    or the __Done__ column (pull request card) and the __Backlog__ column (issue card).

#### Connect Issues

Each time an issue and a pull request are connected, the issue card on Waffle goes under that pull request card as a new merged card. Several issue cards can be linked to a pull request card this way.

In order to connect issues to a pull request, you must use the [Waffle connect Keywords][6]:
  * In the description of the issue.<br>
    When closing the pull request, the issue card will go back to the __Backlog__ column.
  * In the description or the title of the pull request.<br>
    When closing the pull request, the issue will be moved to the __Done__ column and still be merged with the pull request card.

It is also possible to use the [GitHub closing Keywords][5] in the description or the title of a pull request to merge the issue and pull request cards. When closing the pull request the merged card will be moved to the __Done__ column.

#### Create Pull Requests

Before creating a new pull request, a new branch must be created with the id of the issue:

```
git checkout -b solve-issue#3
```

To be interpreted by the __WaffleBot__, the name of the branch must repect some rules:
* `3-solve-issue`: the name starts with the id of the issue, no __'#'__ needed.
* `solve-issue#3`: the name doesn't starts with the id of the issue, the __'#'__ is mendatory.
* `3-solve/issue`: the name is path-like and starts with the id of the issue, no __'#'__ needed.
* `solve/#3-issue`: the name is path-like and doesn't starts with the id of the issue,<br>
                    the issue id must be immediatly after the __'/'__ with a __'#'__.

This will move the card in the column tagged with the __Work Started__ action (here the __In Progress__ column).

When creating a new pull request in order to close an issue, the name or description of that pull request must contain a [GitHub closing Keywords][5] followed by the id of the issue.

This will move the card in the column tagged with either the __New Collaborator PRs__ or __New Contributor PRs__ action (here the __Pending Validation__ column).

To move the card in the __Done__ column, close the pull request. 

## Snippets

### Badge

[![Stories in Ready](https://badge.waffle.io/Kerma0/waffle-automatic.svg?label=ready&title=Ready)](http://waffle.io/Kerma0/waffle-automatic)

The link to this badge can be found under __Project Settings/General__

### Graph

[![Throughput Graph](https://graphs.waffle.io/Kerma0/waffle-automatic/throughput.svg)](https://waffle.io/Kerma0/waffle-automatic/metrics/throughput)

The link to this graph can be found under __Metrics__

[1]: https://waffle.io/
[2]: https://github.com/Kerma0/waffle-automatic/blob/master/img/02.png
[3]: https://github.com/Kerma0/waffle-automatic/blob/master/img/01.png
[4]: https://github.com/integration/wafflebot
[5]: https://help.github.com/articles/closing-issues-via-commit-messages/#keywords-for-closing-issues
[6]: https://github.com/waffleio/waffle.io/wiki/FAQs#prs-connect-keywords
