# morpheus-openapi
OpenAPI documentation for the Morpheus API

## Testing

Using docker:

```
docker run --rm -v $PWD:/spec redocly/openapi-cli lint openapi.yaml --skip-rule no-invalid-media-type-examples
docker run --rm -v $PWD:/tmp -it stoplight/spectral lint -v -F hint "/tmp/openapi.yaml" --ruleset "/tmp/.spectral.json"
```