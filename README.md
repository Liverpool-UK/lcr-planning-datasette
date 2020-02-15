# lcr-planning-datasette

Scripts to deploy the database of LCR planning applications to datasette.  Uses [Travis-CI](https://travis-ci.com) to deploy the latest version to a heroku app

Mostly taken from https://github.com/simonw/fivethirtyeight-datasette.

## Setup

 1. Clone the repo
 1. Get your Morph API token from the end of the download link on the specific scraper's page
 1. Encrypt it with `travis encrypt --pro MORPH_TOKEN="YOUR-MORPH-TOKEN-HERE"`
 1. Replace the `env` -> `global` -> `secure` item at the top of `.travis.yml` with the output of the encrypt command
 1. Get a Heroku auth token with `heroku auth:token`
 1. In the settings for your Travis-CI repository, add an environment variable of `HEROKU_API_KEY` set to the auth token you just got for Heroku
 1. Configure a cron job in Travis-CI to automatically run the build once-a-day (or however often your database should be re-deployed)
