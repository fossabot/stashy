# stashy

Python client for the Atlassian Bitbucket Server (formerly known as Stash) [REST API](https://docs.atlassian.com/bitbucket-server/rest/5.7.0/bitbucket-rest.html). Supports Python 2.6, 2.7 and 3.3.

[![Build Status](https://travis-ci.org/RisingOak/stashy.png?branch=master)](https://travis-ci.org/RisingOak/stashy)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fhamzawix%2Fstashy.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fhamzawix%2Fstashy?ref=badge_shield)

## Installation

```
pip install stashy
```

## Usage
```python
import stashy
stash = stashy.connect("http://localhost:7990/stash", "admin", "admin")
```

## Examples

* Retrieve all groups

```python
stash.admin.groups.list()
```

* Retrieve all users that match a given filter

```python
stash.admin.users.list(filter="admin")
```

* Add a user to a group

```python
stash.admin.groups.add_user('stash-users', 'admin')
```

* Iterate over all projects (that you have access to)

```python
stash.projects.list()
```

* List all the repositories in a given project

```python
stash.projects[PROJECT].repos.list()
```

* List all the commits in a pull request

```python
list(stash.projects[PROJECT].repos[REPO].pull_requests[PULL_REQUEST].commits())
```

* Show the diff of a pull request

```python
stash.project[PROJECT].repos[REPO].pull_requests[PULL_REQUEST].diff()
```

* List all branch restrictions for a repo
```python
stash.projects[PROJECT].repos[REPO].restricted.list()
```

* List all branch permission entities for a repo
```python
stash.projects[PROJECT].repos[REPO].permitted.list()
```

## Implemented

```
/admin/groups [DELETE, GET, POST]
/admin/groups/add-user [POST]
/admin/groups/more-members [GET]
/admin/groups/more-non-members [GET]
/admin/groups/remove-user [POST]
/admin/users [GET, POST, DELETE, PUT]
/admin/users/add-group [POST]
/admin/users/credentials [PUT]
/admin/users/more-members [GET]
/admin/users/more-non-members [GET]
/admin/users/remove-group [POST]
/admin/permissions/groups [GET, PUT, DELETE]
/admin/permissions/groups/none [GET]
/admin/permissions/users [GET, PUT, DELETE]
/admin/permissions/users/none [GET]
/groups [GET]
/projects [POST, GET]
/projects/{projectKey} [DELETE, PUT, GET]
/projects/{projectKey}/permissions/groups [GET, PUT, DELETE]
/projects/{projectKey}/permissions/groups/none [GET]
/projects/{projectKey}/permissions/users [GET, PUT, DELETE]
/projects/{projectKey}/permissions/users/none [GET]
/projects/{projectKey}/permissions/{permission}/all [GET, POST]
/projects/{projectKey}/repos [POST, GET]
/projects/{projectKey}/repos/{repositorySlug} [DELETE, POST, PUT, GET]
/projects/{projectKey}/repos/{repositorySlug}/branches [GET, PUT, DELETE]
/projects/{projectKey}/repos/{repositorySlug}/branches/default [GET, PUT]
/projects/{projectKey}/repos/{repositorySlug}/branches/info/{changesetId} [GET]
/projects/{projectKey}/repos/{repositorySlug}/changes [GET]
/projects/{projectKey}/repos/{repositorySlug}/commits [GET]
/projects/{projectKey}/repos/{repositorySlug}/permissions [GET, POST,DELETE]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests [GET, POST]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId} [GET, PUT]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/activities [GET]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/decline [POST]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/merge [GET, POST]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/reopen [POST]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/approve [POST, DELETE]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/changes [GET]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/comments [POST]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/commits [GET]
/projects/{projectKey}/repos/{repositorySlug}/settings/hooks [GET]
/projects/{projectKey}/repos/{repositorySlug}/settings/hooks/{hookKey} [GET]
/projects/{projectKey}/repos/{repositorySlug}/settings/hooks/{hookKey}/enabled [PUT, DELETE]
/projects/{projectKey}/repos/{repositorySlug}/settings/hooks/{hookKey}/settings [PUT, GET]
/projects/{projectKey}/repos/{repositorySlug}/settings/pull-requests [GET, POST]
/projects/{projectKey}/repos/{repositorySlug}/tags [GET]
/build-status/1.0/commits/{commit-hash} [GET, POST]
```

## Not yet implemented

```
/admin/mail-server [DELETE]
/application-properties [GET]
/hooks/{hookKey}/avatar [GET]
/logs/logger/{loggerName} [GET]
/logs/logger/{loggerName}/{levelName} [PUT]
/logs/rootLogger [GET]
/logs/rootLogger/{levelName} [PUT]
/markup/preview [POST]
/profile/recent/repos [GET]
/projects/{projectKey}/avatar.png [GET, POST]
/projects/{projectKey}/repos/{repositorySlug}/recreate [POST]
/projects/{projectKey}/repos/{repositorySlug}/browse [GET]
/projects/{projectKey}/repos/{repositorySlug}/browse/{path:.*} [GET]
/projects/{projectKey}/repos/{repositorySlug}/commits/{changesetId:.*} [GET]
/projects/{projectKey}/repos/{repositorySlug}/diff/{path:.*} [GET]
/projects/{projectKey}/repos/{repositorySlug}/files [GET]
/projects/{projectKey}/repos/{repositorySlug}/files/{path:.*} [GET]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/comments/{commentId} [DELETE, PUT, GET]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/diff [GET]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/diff/{path:.*} [GET]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/participants [GET, DELETE, POST]
/projects/{projectKey}/repos/{repositorySlug}/pull-requests/{pullRequestId}/watch [POST, DELETE]
/users [GET, PUT]
/users/credentials [PUT]
```


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fhamzawix%2Fstashy.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Fhamzawix%2Fstashy?ref=badge_large)