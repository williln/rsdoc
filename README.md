# rsdoc - Command line utility for interacting with docs.revsys.com

**NOTE**: This utility is useful **ONLY** to [REVSYS](http://www.revsys.com)
clients and staff.

## Installation

To install you can simply run:

    pip install https://github.com/revsys/rsdoc/

## Usage

To create a new template for documentation simply run:

    rsdoc create

**NOTE**: To use the default REVSYS theme you will need to install [hugo](https://gohugo.io/) which for OSX is typically done with a simple `brew install hugo`

To upload docs, finish editing your content, generate it and then run:

    rsdoc upload ./path/to/generated/content/

So the typically workflow becomes:

1. Create docs skeleton using Cookiecutter via `rsdoc create`
1. Edit your docs in `./docs/` using `hugo server` locally to verify everything is working correctly.
1. cd into `./docs/` and run `hugo build`
1. hugo will create a `public/` directory relative to your current path with the built files.
1. To upload these run `rsdoc upload ./public/`

Assuming your `.rsdoc` settings are correct this will tar up the contents of the hugo generated folder and deploy them via REST to docs.revsys.com

## Configuration

`rsdoc` uses an env style file named `.rsdoc` in the current directory.  Here is a simple template that includes all of the values you need:

```
RSDOC_PATH="<Your DocSet Path>"
RSDOC_VERSION="<Your DocSet Version>"
RSDOC_TOKEN="<Your DocSet Token>"
```

These will come from the DocSet model and associated upload Token defined in the system.

## Client, Group, and User management

If you're an admin user of docs.revsys.com you can get and set your API Token in `~/.rsdoc` like this:

```
RSDOC_API_TOKEN="my-token-info"
```

This will allow you to interact with the docs API to manage clients, groups, and putting users into clients and groups.

### rsdoc client usage

To list clients run:

```
rsdoc client --ls
```

## Questions?

Contact Frank
