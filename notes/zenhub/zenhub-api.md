Zenhub API
===

https://github.com/ZenHubIO/API

- Public APIs is very limited.
- API rate limit maximum: 100 requests/minute

# Dependencies

sudo port install jq

# REPO ID

# Issues

```
TOKEN=
ZENHUB_HOST=https://api.zenhub.io
REPO_ID=152184548
ISSUE_NUMBER=55

curl -H 'X-Authentication-Token: '${TOKEN} ${ZENHUB_HOST}/p1/repositories/${REPO_ID}/issues/${ISSUE_NUMBER}

```

# Boards

```
curl -H 'X-Authentication-Token: '${TOKEN} ${ZENHUB_HOST}/p1/repositories/${REPO_ID}/board | jq
```

# Milestone

```
MILESTONE_NUMBER=20190115-20190121%232019-01-21

curl -H 'X-Authentication-Token: '${TOKEN} ${ZENHUB_HOST}/p1/repositories/${REPO_ID}/milestones/${MILESTONE_NUMBER}/start_date
```
