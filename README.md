# NUnit Documentation

This repository serves the content that is found at <http://docs.nunit.org>.

![NUnit Documentation Build Process](https://github.com/nunit/docs/workflows/NUnit%20Documentation%20Build%20Process/badge.svg)

## What is the Docs site? How does it work?

The docs site is a project within the NUnit organization. [Read the vision at VISION.md](VISION.md) to understand more about how the documentation fits into the overall organization and how it supports the other projects.

## How to Build these docs locally

* Prerequisite: Install [docfx](https://dotnet.github.io/docfx/) (using [Chocolatey](https://chocolatey.org/)? The command is `choco install docfx -y`)
* Pull this repository
* `cd docs`
* Run `docfx build`
* Run `docfx serve` and navigate to <http://localhost:8080/_site>

## How to Build These Docs Within GitHub Codespaces

Fancy using GitHub Codespaces for your work on these docs? You can!

* Open the branch you want to work on in GitHub Codespaces
* The tooling, VS code extensions, etc. that we use will immediately be available to you.
* To build, from the in-browser terminal window, run `cd docs` (yes, docs/docs) and run `docfx build`. This will create the `_site` folder.
* To serve within GitHub Codespaces, from the in-browser terminal window, ensure you're in the `docs` directory and run `docfx serve _site -n "*"`. This will forward port 8080 to GitHub Codespaces for you to consume.

We'll be working on follow-ups to make this more user-friendly, but it's now workable.

## Linting Locally

* Install `markdownlint`: `npm install markdownlint-cli -g`
* Open the root of the project (`/`, not `/docs`)
* Run `markdownlint docs/**/*.md`

We'd love your contributions! See [The contributing guide](CONTRIBUTING.md) for how to get involved.

## How the Docs are Built and Deployed

* We build the docs via the GitHub actions located in `./github/workflows`.
* The workflow uses a container with docfx installed; the container builds the docs.
* The workflow then uses another container to push the results to the `gh-pages` branch, using a personal access token that is stored in the repository's settings.
* GitHub serves the outputted site from the `gh-pages` branch, and the DNS of `docs.nunit.org` points there.
