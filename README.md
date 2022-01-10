Source code for the anvi'o community web page served at https://anvio.org

After getting a copy of it, you can run this web page on your local using the following command:

```
bundle exec jekyll serve
```

# Contributing

If you have any questions regarding anything below, please get in touch with us on the anvi'o Slack channel (an up-to-date link is at the top of the front page of https://anvio.org).

## Update / add new anvi'o resources defined in the main page

Please edit the file at `_data/resources.yaml` in this repository. For this, you don't need to do anything with anvi'o, but if the author of the resource is not define din `_data/people.yaml`, you will first have to take care of it. If you'd like to do it yourself, please read the section below on how to 'update people data'. If you don't want to deal with that, please reach out to an anvi'o developer.

Updating the resouces file should be easy. But please note that the order of items in that file should have a logical order from basic to more advanced things within each section. Follow an example for variables and language, and try to use existing tags unless there is certainly a need to define a new one.

## Contribute a blog post or tutorial to be hosted on anvio.org

If you would like to write a blog post or tutorial for the anvi'o web page, anvio.org would be more than happy to host you!

# Upkeeping

A lot of the components of this web page is dynamic, but others require some hands-on upkeeping (at least for now). You can update EVERYTHING all at once by running this command:

``` bash
_scripts/update-all.sh
```

**Please remember**: Everything above and below assumes that you are tracking the development branch of anvi'o, and you are working with an up-to-date repository, unless otherwise is stated. Please don't forget to double-check `git status` to make sure you know what you're about to commit.

The following sections clarify individual updates that are run by `update-all.sh` script. If you run that, you don't need to run any of the ones below, but they're here for posterity.

## Update people data

To update the list of anvi'o authors and contributors, run this (assuming your anvi'o code directory is at `~/github/anvio`):

``` bash
_scripts/update-people-data.sh
```

If there is a new name to be mentioned in `_data/resources.yaml`, this person must be first mentioned in `_data/people.yaml`. If they are not in there, first add their information to either `AUTHORS.yaml` or `CONTRIBUTORS.yaml` in the anvi'o repository, then run the commands above to update the anvio.org repository. Boring, but very important to keep track of people in both repositories.

## Update help pages

Help pages are served at https://anvio.org/help/main or at http://localhost:4000/help/main if you are running the web page on your local.

Never edit the help pages manually or in the anvio.org repository. They are meant to be updated in the anvi'o main repository.

To update the help pages with the latest changes in anvi'o main repository, run this command:

```bash
anvi-script-gen-help-pages -o help/main
```

Triple check `git status` to make sure you know what you're about to commit.

## Update the anvi'o programs and concepts network

The anvi'o network is served at https://anvio.org/network or at http://localhost:4000/network if you are running the web page on your local.

To update the help pages with the latest changes in anvi'o main repository, run this command:

```bash
anvi-script-gen-programs-network -o network/network.json
```
