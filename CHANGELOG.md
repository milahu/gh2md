# Changelog

## 2.0.1 (2022-06-29)

- Fix bug where comments would show the timestamp of the issue instead of the
  timestamp of the comment. Thanks @galenhuntington.


## 2.0.0

- Migrate to the Github v4 GraphQL API. This provides signficantly better
  performance for our use-case compared to the rest API, and it makes
  significantly better use of rate limits. This should make the script much more
  viable for medium-large projects.

  The CLI interface and markdown templates stay the same, but there could be
  some changes in how the data is formatted. For example, in the v4 API pull
  requests will have a `merged` state, whereas previously they were only marked
  as `open` and `closed`.

- Drop dependencies on pygithub and retrying. Add dependencies on requests and
  python-dateutil.


## 1.0.3

- Fix issue where logging the authenticated user errors if the token isn't tied
  to a user (eg. if it's a github action token).


## 1.0.0

- Add support for exporting one file per issue using `--multiple-files`.
- Add support for a token path in `~/.config/gh2md/token`.
- Upgrades to PyGithub 1.55.

Breaking changes:

- Remove support for username + password login, which was removed from the
  Github API back in 2020.

- Remove the `--token` argument. Tokens must now either be read from the
  environment or a file.
