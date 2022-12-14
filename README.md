# morpheus-openapi
OpenAPI documentation for the Morpheus API

## Testing

Using docker:

```shell
docker run --rm -v $PWD:/spec redocly/openapi-cli lint openapi.yaml --skip-rule no-invalid-media-type-examples
docker run --rm -v $PWD:/tmp -it stoplight/spectral lint -v -F hint "/tmp/openapi.yaml" --ruleset "/tmp/.spectral.json"
```

The *test* rake task does the same as above:

```shell
rake test
```

NOTE: The OpenAPI spec is case senstive.  This has caused problems when developing on Windows and Mac.  You may get a good lint with the above commands, but when pushed, it will show any errors in the Actions log.

## Building

Using docker:

```shell
docker run --rm -v $PWD:/spec redocly/openapi-cli bundle openapi.yaml > bundled.yaml
```

The *build* rake task does the same as above:

```shell
rake build
```

This will build the file that we upload to the host, you can use this file in any openapi 3.0.3 renderer.

## Publishing

Pushing to a branch which matches a defined version number with valid secret entry will bundle `openapi.yaml` using redocly-cli and upload to the destination given a good lint.  

Branch name must match version name on destination at https://apidocs.morpheusdata.com

## NOTE

Do not put any documentation into `docs/` where the filename matches a tag in `openapi.yaml`.  Bad things will happen, and we'll have to delete and resync.