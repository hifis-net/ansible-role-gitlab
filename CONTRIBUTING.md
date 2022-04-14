<!--
SPDX-FileCopyrightText: 2022 Helmholtz Centre for Environmental Research (UFZ)
SPDX-FileCopyrightText: 2022 Helmholtz-Zentrum Dresden-Rossendorf (HZDR)

SPDX-License-Identifier: Apache-2.0
-->

# Contributing

## Please Help to Improve this Project 

You would like to contribute to this project and want to know how to do that?
Let me tell you first that you are awesome because you take care!
Let's make this Ansible role even better.
Any contributions and help to improve this project via issues, pull requests
and more are most welcome and much appreciated.

## Why Do We Need Contributors and Contributions

Coding is team-work.
In order to enhance the project or correct bugs and regressions in the project
we need you and your support because the project benefits from your expertise,
knowledge, opinions, perspectives, and labour.
Together we are improving this Ansible role step-by-step.
Please follow these guidelines and be respectful as we respect your work and
your contributions in the same manner and support you and help you with your
contributions.

## Contributions We are Looking For

There are different ways to contribute to this project:

1. Discuss issues and pull requests
2. Create issues
3. Fork the repository and create pull requests
4. Do testing

###  Discuss Issues and Pull Requests

You can contribute by participating in discussions you find in issues and 
pull requests or by starting your own discussions.

### Create Issues

If you found a bug in the Ansible role or a typo in the documentation or
if you would like to clarify functional or quality aspects of the role
you are welcome to create issues to get in contact with us.
Of course, before you do that we ask you to browse through the existing issues
first to make sure that the behaviour you would like to report or enhancement
you would like to request are not covered by other issues already.

### Fork the Repository and Create Pull Requests

If you would like to provide a fix for a bug or a typo in the documentation or
even add or change specific features of the role or specific parts of the
documentation you are welcome to fork this repository, put the suggestion into
a separate branch and create a pull request.
Please also label the pull request, refer to related issues and assign
reviewers that take care of reviewing your suggested changes.
Be aware of the need to test your contributions before opening a pull request.
Of course, before you do that we ask you to browse through the existing
pull requests first to make sure that the bugs you would like to fix or
enhancements you would like to propose are not covered by other pull requests
already.

### Do Testing

Sometimes automated tests are not sufficient to account for specific corner 
cases and to reveal hidden bugs.
Testing the role manually is always a good approach to make sure that the role
also works for other developers.
Even more valuable are of course automated tests because they are repeatable.
Please feel free to support the project by providing automated test cases.
In order to do so you need to fork the repository, put the test cases into
a separate branch and create a pull request.
Please also use labels for your pull request, name issues that you refer to
and assign reviewers who would be able to review your suggested test cases.
Of course, before you do that we ask you to browse through the existing
test cases first to make sure that the test cases you would like to propose
are not covered by other test cases already.

## Contributions Workflow via Pull Requests

If you would like to contribute with pull requests for enhancements, bug-fixes
or test cases, we kindly ask you to follow this workflow:

![Development Workflow](docs/images/workflow.png)

## Guidelines

### Ansible Guides

Because this is an Ansible project we agree with the 
[Ansible Community Guide](https://docs.ansible.com/ansible/latest/community/index.html)
and adhere to the
[Ansible style guide](https://ansible.readthedocs.io/en/stable/dev_guide/style_guide/index.html).

### Linting the Project

Please make sure that your changes are linted before suggesting those changes
in pull requests:

```shell
$ pipenv install --dev
$ pipenv run molecule lint
```

### REUSE Specification Compliance

Each file in this project needs to have a proper license and copyright header.
Please check that each file you add to the project contains license and 
copyright information and that it thereby meets the
[REUSE Specification](https://reuse.software/spec/).

```shell
$ pipenv install --dev
$ pipenv run reuse lint
```

### Testing the Ansible Role

During development of your changes please use the existing automated test cases
to verify that your changes do not break existing test cases:

```shell
$ pipenv install --dev
$ pipenv run molecule test
````

Please consider using
[Ansible Molecule](https://molecule.readthedocs.io/en/latest/)
to write test cases for your suggested changes.
Feel free to add those tests to the GitHub Actions CI Pipeline of this project.

### GitHub Actions CI Pipeline

Make sure that all GitHub Actions CI pipeline jobs pass in your fork before
creating pull requests and that all GitHub Actions CI pipeline jobs pass in
your pull request before assigning reviewers to your pull request.

## How are Contributors Given Credit for Their Valuable Work?

Please add yourself to the list of contributors in file 
[README.md](README.md#contributors) 
via a pull request if you made significant contributions to this role.
Significant contributions are done by suggesting pull requests that fix
bugs or add features or test cases to the project.
Since all other contributions are welcome and may be significant as well 
you can request to be added as a contributor which is then decided on a 
case-by-case basis.

## Ground Rules and Contributions We are Not Looking For

While we welcome and appreciate all contributions we want people to be kind,
respectful and mindful and won't support people who aren't.
