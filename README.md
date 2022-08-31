# publish-integration-image-action

This is a composite action that will publish you image to your Docker Registry.

## Inputs

This action requires uses the following inputs:

| Name               | Type     | Description                                                                        |
|--------------------|----------|------------------------------------------------------------------------------------|
| `package-name`     | String   | Name that the image should be published as to Docker Hub as                        |
| `docker-username`  | String   | Username for the docker account to publish under                                   |
| `docker-password`  | String   | Password for the docker account to publish under                                   |
| `push-to-registry` | String   | Determine if the built image should be pushed to registry (Default is 'false')     |

The docker username and password will likely be passed by `secrets`. You must ensure your repo has access to these secret variables

## Example Usage:

```yaml
jobs:
  ...

  publish-image:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - id: publish-image
        uses: jupiterone/publish-integration-image-action@v1.0.3-beta
        with:
          package-name: 'jupiterone/graph-kubernetes'
          docker-username: ${{ secrets.DOCKERHUB_USERNAME }}
          docker-password: ${{ secrets.DOCKERHUB_TOKEN }}
          push-to-registry: 'true'
```

