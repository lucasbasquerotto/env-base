# Environment Base Repository

This repository has the objective of providing examples of environment files to be used by a Cloud Layer, as described at http://github.com/lucasbasquerotto/cloud#project-environment-base-file.

The directories in this repository are the following:

- [cloud](cloud): Contains examples of environment base files to make deployments in specific Cloud Providers. These files are mainly used as examples in the documentation at http://github.com/lucasbasquerotto/ext-cloud.

- [common](common): General examples of environment base files. The file [main.yml](common/main.yml) is used to deploy a host that has the [controller repository](http://github.com/lucasbasquerotto/ctl) and (optionally) some cron tasks, together with an environment file that is used by the controller layer to deploy projects (this project is mainly used to deploy other projects from a remote host, either due to security, or to deploy continually, or even to deploy faster, in cases in which the deployed host is in the same Cloud Provider and region in which the other projects will be deployed). The file [repos.yml](common/repos.yml) is used to deploy a local project to prepare the environment with specific repositories.

- [demo](demo): Used by demos and some simple (non-production ready) examples.

- [demos](demos): Contains examples of environment base files to deploy some demos.

- [docs](docs): Has examples of deployments that are used in documentations (not necessarily the documentation itself).

- [examples](examples): Contains several examples that can be used as environment base files for production ready projects (but they should be tested carefully before using in a production environment). When deploying a project in a staging or production environment, it's advisable to use these files as a reference and then create your own environment base files with only the necessary to deploy the project, receiving environment specific data (like endpoints and credentials) as parameters from a [project environment file](http://github.com/lucasbasquerotto/cloud#project-environment-file) for each environment (staging, production, etc...).

- [test](test): Contains environment base files to be used in tests ([test.simple.yml](common/test.simple.yml) and [test.yml](common/test.yml)) as well as some files required by these tests.
