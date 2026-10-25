# orchard-public

Deployed on [Orchard](https://docs.orchard.my).

## Image versions

`images.yaml` pins the image of every image-source deployment to an exact release
tag. [Renovate](https://docs.renovatebot.com) opens a PR when a new release comes
out; merging it runs `.github/workflows/deploy.yml`, which rolls the new tag out
through each deployment's Orchard deploy webhook.

Each deployment needs a webhook token in a repo secret named
`ORCHARD_TOKEN_<NAME>` (uppercase, `-` becomes `_`):

```sh
orchard deploy webhook-token create <deployment-id> --label "github actions"
gh secret set ORCHARD_TOKEN_FREE_GAMES
```

To add a deployment, add a line to `images.yaml` and its secret.
