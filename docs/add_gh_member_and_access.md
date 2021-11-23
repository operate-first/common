## Adding GitHub members and managing repo access

All Operate First GitHub members and teams are stored declaratively in the `github-config.yaml` file. Once this file is updated, our
[Peribolos][peri] deployment will bring these changes live. Thus, to add new members or teams and manage team access,
one needs to simply update this file, make a PR, and once merged, the changes will take effect.

## Table of contents

- [Become a Github member](#become-a-github-member)
- [Get repo access](#get-repo-access)
- [Create a GitHub team](#Create-a-GitHub-Team)

### Become a GitHub member
Being a member of the Operate First GitHub org has a couple of perks, some of which include (but not limited to):

- Being able to be assigned GitHub `Issues` in any Operate First repo.
- Create Discussions.
- CI jobs run automatically on PRs without the need for `/ok-to-test` by another member.
- Gain the ability to use certain chat ops commands on issues and pull requests.
- Gain ability to join Operate First GitHub teams and gain elevated access to repos.

To become a GitHub member follow these steps:

1. Fork/Clone the [common repo][crepo].
2. Open `common/github-config.yaml` in a file editor.
3. Add your GitHub handle to `orgs.operate-first.members` list.
4. Commit your changes and make a pull request. This should only require 1 commit.

### Get repo access

We typically do not provide access to our GitHub repositories on an individual basis, instead we provide access to GitHub _teams_. To get access to a specific repo you will need to add your self to a GitHub team. The team should also have access to this repo in question. To do this, follow the steps outlined below:

1. Fork/Clone the [common repo][crepo].
2. Open `common/github-config.yaml` in a file editor.
3. Find your team in `orgs.operate-first.teams`. If your team does not yet exist, create your team by following [these][create-team] instructions.
4. Add your GitHub user handle to `orgs.operate-first.teams.<YOURTEAM>.members`.
5. Ensure that the repo you are looking for access to is listed in `orgs.operate-first.teams.<YOURTEAM>.repos` with the appropriate access level you require. See [GitHub docs][ghroles] for the different types of roles. If the repo is not listed, or does not have the access level you require, you may request it by adding/amending this list accordingly.
6. Commit your changes and make a pull request. This should only require 1 commit (can be combined with commits above).


### Create a GitHub Team

To create your GitHub team follow these steps:

1. Fork/Clone the [common repo][crepo].
2. Open `common/github-config.yaml` in a file editor.
3. Add a new entry to `orgs.operate-first.teams` using the following template:

```yaml
      <team-name>:
        description: <team-dsecription>
        privacy: closed  # Keep as closed, more info: https://docs.github.com/en/rest/reference/teams#create-a-team
        members:
          - <GitHubUser1>
          - <GitHubUser2>
        repos:
          <repo-name-1>: <permission>
          <repo-name-2>: <permission>
```

Fill in the values encapsulated in `<>` as follows:

- `<team-name>`: The GitHub team name to be added within the Operate First Org.
- `<team-description>`: A short description for this team.
- `<GitHubUserN>`: Should be a proper GitHub handle.
- `<repo-name-N>`: Should be a proper Github Repository.
- `<permission>`: Can be one of: read,triage,write,maintain,admin. More info [here][ghroles].

> Note that <repo-name-N> must exist within the org, you can confirm this by ensuring that the repo also exists in
> `orgs.operate-first.repos`, if it does not that means the repo has not been created, follow our [add repo docs][ardocs]

4. Commit your changes and make a [pull request][prdoc]. This should only require 1 commit (can be combined with commits above).

[peri]: https://github.com/kubernetes/test-infra/tree/master/prow/cmd/peribolos
[ghroles]: https://docs.github.com/en/organizations/managing-access-to-your-organizations-repositories/repository-roles-for-an-organization
[ardocs]: add_repo.md
[create-team]: #create-a-github-team
[crepo]: https://github.com/operate-first/common
[prdoc]: https://github.com/operate-first/apps/blob/master/contributing.md#creating-pull-requests
