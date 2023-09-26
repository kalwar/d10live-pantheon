# d10live-pantheon

[![Deployment to Pantheon](https://github.com/kalwar/d10live-pantheon/actions/workflows/deploy_to_pantheon.yml/badge.svg)](https://github.com/kalwar/d10live-pantheon/actions/workflows/deploy_to_pantheon.yml)

A very simple skeleton of Drupal 10 together with pantheon site powering your live site, a website about whatever you want it to be.

- [Local setup](#setup)
- [Making site changes](#changes)
- [Deployment to Pantheon via Github actions](#deployment)

## Local site setup with DDEV <a name="setup"></a>

Do the lando setup, make sure you can clone the repo from pantheon site and run locally drupal 10 with lando

## Making site changes <a name="changes"></a>

### Configuration changes

Drupal 10 configuration (such as content type and field definitions) is managed through yml files. These files live in the `config` directory.

After you make configuration changes locally (such as adding a field to a content type), you can then export those changes by running `lando drush cex` in the project directory.

Import site database, clear caches, and apply site configuration from code.

1. `lando db-export`
2. You will get database.sql.gz file in root of your project folder
3. Copy database dump generated e.g. `database.sql.gz` dump to pantheon site Database/Files under "Import" section
4. Make sure you have File option selected
5. Your lando drupal local site configurations must match with pantheon site

## Deployment to Pantheon via Github Actions <a name="deployment"></a>

This site's main branch is automatically committed and deployed to Pantheon's dev environment with a [Github action workflow file](.github/workflows/deploy_to_pantheon.yml). The pantheon site name and ID are configured in that file.

It needs these secrets added to this repository's Github settings:

- **PANTHEON_SSH_PRIVATE_KEY**
  <br>(A Private SSH key paired to a [Public SSH key added to Pantheon](https://docs.pantheon.io/ssh-keys))
- **TERMINUS_TOKEN**
  <br>(A generated [Pantheon Machine token](https://docs.pantheon.io/machine-tokens))
