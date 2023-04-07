# Development Environment

## Dependencies

* Ruby 2.7.3
* bundler 2.2.16
* Node 14
* chromedriver
* tmux

To avoid having to install and manage these dependencies you can use the Postfacto [Docker image](https://hub.docker.com/r/postfacto/dev/) for development:

```bash
./docker.sh
cd postfacto
```

## Installing library dependencies

Before development you'll need to install library dependencies (gems and npm packages) for the `web`, `api` and `e2e` codebases by running:

```bash
./deps.sh
```

## Running locally

You can run Postfacto locally at <http://localhost:3000> by running:

```bash
./run.sh
```

Or to use real authentication (this will use no authentication unless `config.js` has a Google Auth client ID):

```bash
./run.sh --real-auth
```

---

The admin dashboard will be available at <http://localhost:4000/admin>.

A default admin user `email@example.com` with password `password` will be created

You can create other admin users using the following rake task in the `api` directory:

```bash
ADMIN_EMAIL=email@example.com ADMIN_PASSWORD=password rake admin:create_user
```

## Running tests

You can run the tests for the whole project in the root directory by simply running:

```bash
./test.sh
```

The following sections show how to run individual test suites during development.

### Web

To run the tests in "watch mode" (runs any tests touched by unstaged Git changes and re-runs tests when files change):

```bash
cd web
npm test
```

(this can also be written as `npm --prefix=web test` if you prefer).

To run all the tests:

```bash
cd web
CI=true npm test
```

Note that the frontend tests will run significantly faster outside the docker container.
If you want to do this, you will need to install the dependencies again (due to architecture differences):

```bash
cd web
npm install
npm test
```

Both installations can coexist; the docker container will use dependencies located in docker_node_modules.

### API

```bash
cd api
bundle exec rake
```

### End to end

```bash
./e2e.sh
```

# Contributing

We’d love to accept your patches and contributions to this project.

## Code reviews

All submissions, including submissions by project members, require review and we use GitHub's pull requests for this purpose. Please consult [GitHub Help](https://help.github.com/articles/about-pull-requests/) if you need more information about using pull requests.

## Giving yourself credit

We maintain a [humans.txt](humans.txt) file so that we can keep a list of all the people that have contributed throughout the development of Postfacto. If you'd like to add yourself feel free to do so as part of a Pull Request by putting your name and contact info (if you'd like) in the 'CONTRIBUTORS' section.
