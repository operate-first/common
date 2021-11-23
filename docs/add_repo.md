## Adding a Repo
All Operate First GitHub repositories are stored declaratively in the `github-config.yaml` file. To add a new repo we
need to update this file, and then our [Peribolos][peri] deployment will bring these changes live.

Follow the steps outlined below to add your repo:

1. Fork/Clone the [common repo][crepo].
2. Open `common/github-config.yaml` in a file editor.
3. Add your new repo to `orgs.operate-first.repos` by appending this list, use the following template:
```yaml
  <repo-name>:
    description: <repo-description>
    has_projects: false
```
Fill in the values encapsulated in`<>` as follows:

- `<repo-name>`: Name of the GitHub repo
- `<repo-description`: Short repo description (this will appear at the top of the repo).

You can find a full list of available parameters [here][repo-api].

4. Commit your changes and make a [pull request][prdoc]. This should only require 1 commit.

[peri]: https://github.com/kubernetes/test-infra/tree/master/prow/cmd/peribolos
[repo-api]: https://docs.github.com/en/github-ae@latest/rest/reference/repos#create-an-organization-repository
[crepo]: https://github.com/operate-first/common
[prdoc]: https://github.com/operate-first/apps/blob/master/contributing.md#creating-pull-requests
