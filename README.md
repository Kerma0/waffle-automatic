# How to use Waffle Automatic Work Tracking at Pryv

This is an empty repository to help setup __Waffle__ boards and use the __Automatic Work Tracking__.

This guide is meant for [__Pryv__][Pryv URL] developers, be aware there are many other ways to use __Waffle__.

## Setup the Waffle board

* Go to the [__Waffle home page__][Waffle URL] and __log in__.
* Add your repository using the ![Add Project Button][Add Project IMG] button.
* Customize your board in the __Project Settings__ / __Columns__ menu, located in the __Waffle left bar__:
  - Add the column __*Pending Validation*__ (you must choose a label, create the label __pending__ with color __#4d9a11__).
  - Define the columns on which the issues and pull requests will be moved by the __Automatic Work Tracking__:
    * Drag and drop the __Work Started__ action under the __*In Progess*__ column.
    * Drag and drop the __New Contributor PRs__ action under the __*Pending Validation*__ column.
    * Drag and drop the __New Collaborator PRs__ action under the __*Pending Validation*__ column.

![Columns Settings Example][Columns Settings IMG]

## Use the Automatic Work Tracking

Install the [__WaffleBot__][WaffleBot URL] on __GitHub__, be sure to select only the repository you wish to monitor.

#### Create an Issues

The issue can be created either on __GitHub__ or directly in the __Waffle board__.<br>
It will automatically appear under the __Backlog__ column.

Once you're ready to start solving the issue or you current work solves the issue, place it under the __*Ready*__ column.

#### Working on an Issue

If your current work is related to an issue, you should place this issue to the __*In Progress*__ column:
  * Manually: simply drag and drop the card in the column.
  * Automatically: create a new branch containing the id of the issue (e.g: `git checkout -b solve-issue#3`).

Beware, the name of the branch must respect some rules (note that the __'-'__ can be replace by __'_'__):
  * If the name starts with the id: `3-solve-issue`.
  * If the name doesn't start with the id: `solve-issue#3` or `solve-#3-issue`.
  * If the name is path-like and starts with the id: `3-solve/issue`.
  * If the name is path-like and doesn't starts with the id: `solve/#3-issue`.

#### Create a pull request

While creating the pull request, link the related issues in the description of that pull request using [__GitHub closing Keywords__][Closing Keywords URL].<br>
This will move the issue cards in the __*Pending Validation*__ column and link the pull request to all issue cards it refers to.

#### Close the pull request

When closing the pull request all linked issue cards will be moved to the __*Done*__ column.

## Snippets

### Badge

[![Stories in Ready](https://badge.waffle.io/Kerma0/waffle-automatic.svg?label=ready&title=Ready)](http://waffle.io/Kerma0/waffle-automatic)

The link to this badge can be found in the __Project Settings__ / __General__ menu, located in the __Waffle left bar__.

### Graph

[![Throughput Graph](https://graphs.waffle.io/Kerma0/waffle-automatic/throughput.svg)](https://waffle.io/Kerma0/waffle-automatic/metrics/throughput)

The link to this graph can be found in the __Metrics__ menu, located in the __Waffle left bar__.

[Pryv URL]: http://pryv.com/
[Waffle URL]: https://waffle.io/
[WaffleBot URL]: https://github.com/integration/wafflebot
[Closing Keywords URL]: https://help.github.com/articles/closing-issues-via-commit-messages/#keywords-for-closing-issues

[Columns Settings IMG]: https://github.com/Kerma0/waffle-automatic/blob/master/img/01.png
[Add Project IMG]: https://github.com/Kerma0/waffle-automatic/blob/master/img/02.png
