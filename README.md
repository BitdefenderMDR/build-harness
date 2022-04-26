
<!-- markdownlint-disable -->
# Build Harness [![docker](https://github.com/BitdefenderMDR/build-harness/actions/workflows/docker.yml/badge.svg)](https://github.com/BitdefenderMDR/build-harness/actions/workflows/docker.yml) [![lint](https://github.com/BitdefenderMDR/build-harness/actions/workflows/lint.yml/badge.svg)](https://github.com/BitdefenderMDR/build-harness/actions/workflows/lint.yml)
<!-- markdownlint-restore -->


[![Bitdefender][logo]](https://bitdefender.com)


<!--




  ** DO NOT EDIT THIS FILE
  **
  ** This file was automatically generated by the `auto-readme`.
  ** 1) Make all changes to `README.yaml`
  ** 2) Run `make init` (you only need to do this once)
  ** 3) Run`make readme` to rebuild this file.
  **
  **




-->

This `build-harness` is a collection of Makefiles to facilitate building README files and can be expanded to do more.
It's designed to work with CI/CD systems such as GitHub Actions, Codefresh, Travis CI, CircleCI and Jenkins.

---


It's 100% Open Source and licensed under the [APACHE2](LICENSE).












## Usage

**Ensure you have [`fetch`](https://github.com/gruntwork-io/fetch) installed and in your path.**

At the top of your `Makefile` add, the following...

```make
-include $(shell fetch --log-level=error --repo=https://github.com/bitdefendermdr/build-harness --source-path=templates/Makefile.build-harness --branch=master .build-harness 2>/dev/null; echo .build-harness)
```

This will download a `Makefile` called `.build-harness` and include it at runtime. We recommend adding the `.build-harness` file and `build-harness` directory to your `.gitignore`.

This automatically exposes many new targets that you can leverage throughout your build & CI/CD process.

Run `make help` for a list of available targets.

**NOTE:** the `/` is interchangable with the `:` in target names

Run `make readme/init` to create a generic README.yml. Update content with the details of what should be in the README.md

Run `make readme` to build the README.md. **This will overwrite the current README.md if one exists.**

Before committing files, run `make pr/auto-format` to formart files (awk outputs slightly differently in alpine than the real world).

## Quick Start

Here's how to get started...

1. `git clone git@github.com:BitdefenderMDR/build-harness.git` to pull down the repository
1. `make init` to intialize the [`build-harness`](https://github.com/BitdefenderMDR/build-harness)


## Examples

Here is an example:
- [`terraform-null-label`](https://github.com/cloudposse/terraform-null-label/) - A terraform module that leverages `readme`, `terraform/%` and `docs/%` targets. Some of the `terraform/%` targets were removed and some new targets were added.

### Contributing additional modules
When you make changes to the repo, ensure you build a new docker image locally `make docker/build` to ensure the image will be successful after the merge.
In addition to creating the image locally run `make pr/auto-format` to ensure the README.md is up-to-date.



<!-- markdownlint-disable -->
## Makefile Targets
```text
Available targets:

  bash/lint                           Lint all bash scripts
  checkov/install                     Install checkov
  checkov/run                         Static code security analysis
  clean                               Clean build-harness
  docker/build                        Build docker image
  docker/clean                        Cleanup docker.                     WARNING!!! IT WILL DELETE ALL UNUSED RESOURCES
  docker/clean/containers             Cleanup docker containers.          WARNING!!! IT WILL DELETE ALL UNUSED CONTAINERS
  docker/clean/images                 Cleanup docker images.              WARNING!!! IT WILL DELETE ALL UNUSED IMAGES
  docker/clean/images/all             Cleanup docker images all.          WARNING!!! IT WILL DELETE ALL IMAGES
  docker/clean/networks               Cleanup docker networks.            WARNING!!! IT WILL DELETE ALL UNUSED NETWORKS
  docker/clean/volumes                Cleanup docker volumes.             WARNING!!! IT WILL DELETE ALL UNUSED VOLUMES
  docker/image/promote/local          Promote $SOURCE_DOCKER_REGISTRY/$IMAGE_NAME:$SOURCE_VERSION to $TARGET_DOCKER_REGISTRY/$IMAGE_NAME:$TARGET_VERSION
  docker/image/promote/remote         Pull $SOURCE_DOCKER_REGISTRY/$IMAGE_NAME:$SOURCE_VERSION and promote to $TARGET_DOCKER_REGISTRY/$IMAGE_NAME:$TARGET_VERSION
  docker/image/push                   Push $TARGET_DOCKER_REGISTRY/$IMAGE_NAME:$TARGET_VERSION
  docker/login                        Login into docker hub
  docs/targets.md                     Update `docs/targets.md` from `make help`
  docs/terraform.md                   Update `docs/terraform.md` from `terraform-docs`
  flake8/install                      Install flake8
  git/export                          Export git vars
  github/init                         Initialize GitHub directory with default .github files
  github/vendor                       Create the vendor directory and add gitignore
  help                                Help screen
  help/all                            Display help for all targets
  help/short                          This help short screen
  init                                Init build-harness
  make/lint                           Lint all makefiles
  packages/delete                     Delete packages
  packages/install                    Install packages
  packages/install/%                  Install package (e.g. helm, helmfile, kubectl)
  packages/reinstall                  Reinstall packages
  packages/reinstall/%                Reinstall package (e.g. helm, helmfile, kubectl)
  packages/uninstall/%                Uninstall package (e.g. helm, helmfile, kubectl)
  readme                              Alias for readme/build
  readme/build                        Create README.md by building it from README.yaml
  readme/init                         Create basic minimalistic .README.md template file
  readme/lint                         Verify the `README.md` is up to date
  terraform/fmt                       Format Terraform
  terraform/install                   Install terraform
  terraform/lint                      Lint check Terraform
  terraform/validate                  Basic terraform sanity check
  tflint/install                      Install tflint
  tflint/run                          A Pluggable Terraform Linter
  tfsec/install                       Install tfsec
  tfsec/run                           Static code security analysis

```
<!-- markdownlint-restore -->



## Related Projects

Check out these related projects.

- [Packages](https://github.com/cloudposse/packages) - Cloud Posse installer and distribution of native apps
- [Dev Harness](https://github.com/cloudposse/dev) - Cloud Posse Local Development Harness


## References

For additional context, refer to some of these links.

- [Cloudposse - Build Harness](https://github.com/cloudposse/build-harness) - The `build-harness` is a slimmed down version of the Cloudposse "Build Harness"



## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/BitdefenderMDR/build-harness/issues) to report any bugs or file feature requests.

### Developing

In general, PRs are welcome. We follow the typical "shared repository" Git workflow.

1. **Clone** the project to your own machine
1. **Create** a feature branch
1. **Commit** changes to branch
1. **Push** your work back up to the feature branch
1. Submit a **Pull Request** to **test** then **dev** finally to **master/main** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!


[logo]: https://www.bitdefender.com/etc.clientlibs/bitdefender/clientlibs/clientlib-site/resources/images/aem/black_company_logo.svg
