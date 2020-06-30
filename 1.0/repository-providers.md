# Repository providers

Deploy currently supports the following providers:

- Bitbucket
- Github

## Bitbucket

Include the following variables in your `.env` file.

```bash
BITBUCKET_OAUTH_KEY=client_id
BITBUCKET_OAUTH_SECRET=client_secret
```

Please follow the [official Bitbucket docs](https://confluence.atlassian.com/bitbucket/oauth-on-bitbucket-cloud-238027431.html) on how to create an OAuth consumer.

Callback URL: `https://yoursite.com/deploy/authorize/bitbucket/access`

Permissions: `projects:read`, `account:read`, `webhooks:read and write`

## Github

Include the following variables in your `.env` file.

```bash
GITHUB_OAUTH_KEY=client_id
GITHUB_OAUTH_SECRET=client_secret
```

Please follow the [official Github docs](https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/) on how to create an OAuth app.

Callback URL: `https://yoursite.com/deploy/authorize/github/access`
