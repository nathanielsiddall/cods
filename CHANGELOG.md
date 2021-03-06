2.0.1

- bugfix: fix site restart in post-receive hook

2.0.0

- added: Interactive help (`cods help`). Interactive walkthroughs for various
  deployment scenarios. Currently only contains help for deploying java projects
- added: The ability to deploy node applications
- added: Site type specifications to the site creation process. One of `--java`,
  `--node`, or `--static`
- added: port number specification when creating a site. The port that the
  application will run on must now be specified
- added: `ports` subcommand to view ports being proxied to based on the nginx
  configuration files for each site
- added: The post-receive git hook for each site type will now only build and
  deploy when the master branch is pushed.
- removed: `log:tail` and `log:follow` subcommands commands. Logs are now
  accessible through the `site logs` subcommand.
- removed: Tomcat. All sites will need to be a self-contained web server. For
  our primary use case, deploying spring boot applications, we will not need to
  do too much different, and, in fact, we will actually have a little less
  configuration to do.
- removed: `site deploy` subcommand. Since we are no longer using tomcat and
  have a wide variety of site types, this no longer makes sense to keep.
- refactor: Individual sites are now managed through a systemd service unit.
  This includes logs for each application as well.
- refactor: most permissions. Each application will have a user and group
  created for it, and the relevant files/directories for each site will be used
  by that user and group.
- refactor: rename `.build_config` to `.cods`
- refactor: site creation. When creating a site, specifying a site type is now
  mandatory (one of `--java`, `--node`, or `--static`), and for java and node
  sites, a port number that the application will run on must be specified
- tests: refactored as necessary to reflect differences in permissions / site
  setup
- tests: added tests that fully deploy an application and ensure that the
  expected response is received from the application (`tests/deploy.sh`)
- docs: Updated to reflect all the changes outlined above
- docs: Added some documentation on deploying a node site

1.2.2

- bugfix: fix typo in `adduser` help message

1.2.1

- minor enhancement: add version information to `info` subcommand
- bugfix: quote variables that should be quoted

1.2.0

- feature: enhance the `adduser` subcommand; add users to the server with a
  github username
- bugfix: Don't create the data directory for a command if the server setup fails

1.1.0

- feature: add server command for enabling a swapfile

1.0.0

- docs: more of them

There isn't really much new here, but the api is stable enough to commit to and
create a v1.

0.2.3

- enhancement: add version information to `cods` command

0.2.2

- bugfix: credentials are no longer recorded if user creation fails (26caf81)
- tests: make the testing setup easier
- tests: add tests for site removal

0.2.1

- bugfix/enhancement: remove unneccesary sudo

0.2.0

- refactor to separate scripts for individual server management (user-defined)
  and server setup (`cods`)
