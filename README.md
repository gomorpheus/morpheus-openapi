# morpheus-openapi
OpenAPI documentation for the Morpheus API

## Testing

Using docker:

```
docker run --rm -v $PWD:/spec redocly/openapi-cli lint openapi.yaml --skip-rule no-invalid-media-type-examples
docker run --rm -v $PWD:/tmp -it stoplight/spectral lint -v -F hint "/tmp/openapi.yaml" --ruleset "/tmp/.spectral.json"
```

## Publishing

Pushing to a branch which matches a defined version number with valid secret entry will bundle `openapi.yaml` using redocly-cli and upload to the destinatio given a good lint.  

Branch name must match version name on destination at https://apidocs2.morpheusdata.com