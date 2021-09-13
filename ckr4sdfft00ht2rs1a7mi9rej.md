## GitHub REST API

Most of us use GitHub services frequently if not on a daily basis. 

If you are a student, GitHub offers student packages with great tools and freebies you could use. Check my article on [Github's Developer Pack for students](https://chrisdevcode.hashnode.dev/github-students-developer-pack).

In this article, I will take you through using GitHub REST API to display your repos on your portfolio website. I will use [postman](http://postman.com/) to test the API.

[GitHub REST API Documentation](https://docs.github.com/en/rest).

## Playing With The API

I'll use  [postman](https://chrisdevcode.hashnode.dev/using-postman-like-a-pro)  to show you what the API can offer for your own personal use. For this, I'll be using the endpoint to fetch a user's repositories.

```
https://api.github.com/users/{github_username}
https://api.github.com/users/{github_username}/repos
```

![Postman Screenshot](https://cdn.hashnode.com/res/hashnode/image/upload/v1626342617407/nEm1m4pQl.png)

![Postman Screenshot](https://cdn.hashnode.com/res/hashnode/image/upload/v1626342060506/oxI1ZjT2k.png)

### Using the GitHub User endpoint:

```
https://api.github.com/users/{github_username}
```

i.e:

```
https://api.github.com/users/achingachris
```

This returns GitHub user details:

```JSON
{
    "login": "",
    "id": ,
    "node_id": "",
    "avatar_url": "",
    "gravatar_id": "",
    "url": "",
    "html_url": "https://github.com/achingachris",
    "followers_url": "https://api.github.com/users/achingachris/followers",
    "following_url": "https://api.github.com/users/achingachris/following{/other_user}",
    "gists_url": "https://api.github.com/users/achingachris/gists{/gist_id}",
    "starred_url": "https://api.github.com/users/achingachris/starred{/owner}{/repo}",
    "subscriptions_url": "https://api.github.com/users/achingachris/subscriptions",
    "organizations_url": "https://api.github.com/users/achingachris/orgs",
    "repos_url": "https://api.github.com/users/achingachris/repos",
    "events_url": "https://api.github.com/users/achingachris/events{/privacy}",
    "received_events_url": "https://api.github.com/users/achingachris/received_events",
    "type": "User",
    "site_admin": false,
    "name": "chrisdevcode",
    "company": null,
    "blog": "",
    "location": "Kenya",
    "email": null,
    "hireable": null,
    "bio": "React | Next | Node | C#(dotnet)\r\n\r\nTech Community Lover",
    "twitter_username": null,
    "public_repos": 211,
    "public_gists": 15,
    "followers": 91,
    "following": 117,
    "created_at": "2019-04-29T22:17:15Z",
    "updated_at": "2021-07-15T06:56:22Z"
}
```

You could use this to display:


1. Public respos and gists
2. Date you created your GitHub account
3. GitHub bio
4. Number of people you follow and followers too.

### Using the GitHub User Repos endpoint:

```
https://api.github.com/users/{github_username}/repos
```

i.e:


```
https://api.github.com/users/achingachris/repos
```

The results returned:

PS - It also returns the user details plus all the repos:

```JSON
{
        "id": 300814209,
        "node_id": "MDEwOlJlcG9zaXRvcnkzMDA4MTQyMDk=",
        "name": "AI-ML-Bootcamp",
        "full_name": "achingachris/AI-ML-Bootcamp",
        "private": false,
        "owner": {
            "login": "achingachris",
            "id": 50122165,
            "node_id": "MDQ6VXNlcjUwMTIyMTY1",
            "avatar_url": "https://avatars.githubusercontent.com/u/50122165?v=4",
            "gravatar_id": "",
            "url": "https://api.github.com/users/achingachris",
            "html_url": "https://github.com/achingachris",
            "followers_url": "https://api.github.com/users/achingachris/followers",
            "following_url": "https://api.github.com/users/achingachris/following{/other_user}",
            "gists_url": "https://api.github.com/users/achingachris/gists{/gist_id}",
            "starred_url": "https://api.github.com/users/achingachris/starred{/owner}{/repo}",
            "subscriptions_url": "https://api.github.com/users/achingachris/subscriptions",
            "organizations_url": "https://api.github.com/users/achingachris/orgs",
            "repos_url": "https://api.github.com/users/achingachris/repos",
            "events_url": "https://api.github.com/users/achingachris/events{/privacy}",
            "received_events_url": "https://api.github.com/users/achingachris/received_events",
            "type": "User",
            "site_admin": false
        },
        "html_url": "https://github.com/achingachris/AI-ML-Bootcamp",
        "description": "Artificial Intelligence and Machine Learning Bootcamp - Strathmore University",
        "fork": false,
        "url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp",
        "forks_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/forks",
        "keys_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/keys{/key_id}",
        "collaborators_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/collaborators{/collaborator}",
        "teams_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/teams",
        "hooks_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/hooks",
        "issue_events_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/issues/events{/number}",
        "events_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/events",
        "assignees_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/assignees{/user}",
        "branches_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/branches{/branch}",
        "tags_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/tags",
        "blobs_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/git/blobs{/sha}",
        "git_tags_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/git/tags{/sha}",
        "git_refs_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/git/refs{/sha}",
        "trees_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/git/trees{/sha}",
        "statuses_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/statuses/{sha}",
        "languages_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/languages",
        "stargazers_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/stargazers",
        "contributors_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/contributors",
        "subscribers_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/subscribers",
        "subscription_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/subscription",
        "commits_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/commits{/sha}",
        "git_commits_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/git/commits{/sha}",
        "comments_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/comments{/number}",
        "issue_comment_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/issues/comments{/number}",
        "contents_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/contents/{+path}",
        "compare_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/compare/{base}...{head}",
        "merges_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/merges",
        "archive_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/{archive_format}{/ref}",
        "downloads_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/downloads",
        "issues_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/issues{/number}",
        "pulls_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/pulls{/number}",
        "milestones_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/milestones{/number}",
        "notifications_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/notifications{?since,all,participating}",
        "labels_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/labels{/name}",
        "releases_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/releases{/id}",
        "deployments_url": "https://api.github.com/repos/achingachris/AI-ML-Bootcamp/deployments",
        "created_at": "2020-10-03T06:39:03Z",
        "updated_at": "2020-10-07T19:30:57Z",
        "pushed_at": "2020-10-07T19:30:54Z",
        "git_url": "git://github.com/achingachris/AI-ML-Bootcamp.git",
        "ssh_url": "git@github.com:achingachris/AI-ML-Bootcamp.git",
        "clone_url": "https://github.com/achingachris/AI-ML-Bootcamp.git",
        "svn_url": "https://github.com/achingachris/AI-ML-Bootcamp",
        "homepage": "",
        "size": 140,
        "stargazers_count": 1,
        "watchers_count": 1,
        "language": "Jupyter Notebook",
        "has_issues": true,
        "has_projects": true,
        "has_downloads": true,
        "has_wiki": true,
        "has_pages": false,
        "forks_count": 0,
        "mirror_url": null,
        "archived": false,
        "disabled": false,
        "open_issues_count": 0,
        "license": {
            "key": "mit",
            "name": "MIT License",
            "spdx_id": "MIT",
            "url": "https://api.github.com/licenses/mit",
            "node_id": "MDc6TGljZW5zZTEz"
        },
        "forks": 0,
        "open_issues": 0,
        "watchers": 1,
        "default_branch": "main"
    },
```

From this, you could use this to show your GitHub repos' details with much ease.

To explore more on using the GitHub REST API for Users, visit: 

https://docs.github.com/en/rest/reference/users

## Next Step

Check out my Blog for a tutorial on using the GitHub API in a NEXTJS app.


