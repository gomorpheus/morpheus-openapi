# morpheus-openapi
OpenAPI documentation for the Morpheus API

## Testing

Using docker:

```
docker run --rm -v $PWD:/spec redocly/openapi-cli lint openapi.yaml --skip-rule no-invalid-media-type-examples
docker run --rm -v $PWD:/tmp -it stoplight/spectral lint -v -F hint "/tmp/openapi.yaml" --ruleset "/tmp/.spectral.json"
```

NOTE: The OpenAPI spec is case senstive.  This has caused problems when developing on Windows and Mac.  You may get a good lint with the above commands, but when pushed, it will show any errors in the Actions log.

## Building

Using docker:

```
docker run --rm -v $PWD:/spec redocly/openapi-cli bundle openapi.yaml > bundled.yaml
```

This will build the file that we upload to the host, you can use this file in any openapi 3.0.3 renderer.

## Publishing

Pushing to a branch which matches a defined version number with valid secret entry will bundle `openapi.yaml` using redocly-cli and upload to the destination given a good lint.  

Branch name must match version name on destination at https://apidocs2.morpheusdata.com