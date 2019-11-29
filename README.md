# Suggestic

[https://suggestic.github.io/api-docs/](https://suggestic.github.io/api-docs/)

### Prerequisites

You're going to need:

 - **Linux or macOS** — Windows may work, but is unsupported.
 - **Ruby, version 2.3.1 or newer**
 - **Bundler** — If Ruby is already installed, but the `bundle` command doesn't work, just run `gem install bundler` in a terminal.

### Getting Set Up

1. Fork this repository on GitHub.
2. Clone *your forked repository* (not our original one) to your hard drive with `git clone https://github.com/YOURUSERNAME/slate.git`
3. `cd slate`

```shell
# either run this to run locally
bundle install
bundle exec middleman server
```

### Deployment
```
./deploy.sh
```