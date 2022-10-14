# Rake tasks for morpheus-openapi repository

PROJECT_ROOT = `git rev-parse --show-toplevel`.strip
BUILD_DIR    = File.join(PROJECT_ROOT, "build")

desc "Validates schema by executing lint commands via docker"
task :validate => ["docker:lint"]

desc "Builds bundled.yaml with redocly via docker "
task :build => ["docker:build"]

namespace "docker" do

  # Ensure docker is installed
  task :is_installed do
    sh "which docker", verbose: false do |ok, status|
      unless ok
        fail "System command `docker` was not found.\nCommand failed with status (#{status.exitstatus}): [which docker]"
      end
    end
  end

  #desc "Validate the openapi schema with both redocly and spectral"
  task :lint => [:redocly_lint, :spectral_lint]

  #desc "Executes `redocly/openapi-cli lint` using docker"
  task :redocly_lint => [:is_installed] do
  	cd PROJECT_ROOT, verbose: false do
		  sh("docker run --rm -v $PWD:/spec redocly/openapi-cli lint openapi.yaml --skip-rule no-invalid-media-type-examples")
    end
  end

  #desc "Executes `stoplight/spectral lint` using docker"
  task :spectral_lint => [:is_installed] do
    cd PROJECT_ROOT, verbose: false do
      sh("docker run --rm -v $PWD:/tmp -it stoplight/spectral lint -v -F hint \"/tmp/openapi.yaml\" --ruleset \"/tmp/.spectral.json\"")
    end
  end

  #desc "Executes `stoplight/spectral lint` using docker"
  task :build => [:is_installed] do
    cd PROJECT_ROOT, verbose: false do
      sh("docker run --rm -v $PWD:/spec redocly/openapi-cli bundle openapi.yaml > bundled.yaml")
    end
  end
end

