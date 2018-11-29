# AppEngine npm

Private npm registry using [Verdaccio](https://verdaccio.org)
running on Google AppEngine with [GitHub](https://github.com)
authentication.

This uses the node.js AppEngine Standard Runtime and because
npm isn't something you are typically accessing all the time,
AppEngine's ability to scale down to zero when not being used
means it will usually stay within the daily free usage limit.

## Dependencies

The following packages are used:

* [Verdaccio](https://github.com/verdaccio)
* [Verdaccio plugin for Google Cloud Storage](https://github.com/verdaccio/verdaccio-google-cloud)
* [Verdaccio plugin for GitHub OAuth](https://github.com/n4bb12/verdaccio-github-oauth-ui)

## Usage

Install using:

    npm install

The Verdaccio configuration settings are stored in `config.yaml`
and should be adjusted to match your GitHub organization, scope
in npm and DNS name for your npm registry. When using a custom
domain name you can use a `dispatch.yaml` file to route requests
to the correct AppEngine service (npm) if you have others in the
same project (otherwise, make this service the default).

Follow the instructions for the plugins and set the appropriate
config settings for the Google Cloud Storage bucket, the GitHub 
OAuth keys and the organization / package settings you required.

With your project selected in Google Cloud CLI, deploy using:

    gcloud app deploy

Or, alternatively, set the project in the deploy command, e.g.:

    gcloud app deploy --project captain-codeman
