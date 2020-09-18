# CDF Hacktoberfest Information
Information and guidelines for participating in the CDF's Hacktoberfest program

## Where To Work

In order to receive CDF-tracked points for your open source GitHub contribution activity during Hacktoberfest, you must work in one of the tracked organizations. These include CDF project organzations:

- [Jenkins](https://github.com/jenkinsci)
- [Jenkins X](https://github.com/jenkins-x)
- [Screwdriver](https://github.com/screwdriver-cd)
- [Spinnaker](https://github.com/spinnaker)
- [Tekton](https://github.com/tektoncd)

And these organizations:
- [CDF-Hacktoberfest](https://github.com/cdf-hacktoberfest)
- [Spinnaker-Hackathon](https://github.com/spinnaker-hackathon)

To build demos, plugins, or automation that are related to CDF projects but cannot be immediately contributed to the project organizations themselves, create repositories to store the work in this [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest) organization. Content contributions like blog posts, solution briefs, whitepapers, training resources, or video scripts should also be initiated as respositories in the [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest) organization. 

This will facilitate easy tracking and review of all contributions from the participating CDF community. All participants will be added to the [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest) organization after checking in to the event and providing a GitHub username on the [check-in form](link@link.com).

## Points Eligibility

The CDF Project Outreach team will track and tally points based on GitHub activity in eligible organizations, and other eligible content contributions as tracked in the  and in [Slack](link-to-Slack-channel).

We will use the following query against the [GH Archive dataset of public GitHub activity](https://www.gharchive.org/) to track contributions according to organization name:

```
SELECT
  actor.login,
  COUNT(*) as cnt,
FROM
  `githubarchive.month.*`
WHERE
  (repo.name LIKE 'spinnaker/%' OR  repo.name LIKE 'spinnaker-hackathon/%' OR repo.name LIKE 'jenkinsci/%' OR repo.name LIKE 'ExitoLab/examplePluginRepository' OR repo.name LIKE 'carvanitis/spingarden-training')
  AND created_at >= '2020-07-16 00:00:00'
  AND created_at < '2020-07-23 19:00:00'
  AND _TABLE_SUFFIX > '2020'
  AND type IN ('IssuesEvent',
    'IssueCommentEvent',
    'PullRequestReviewCommentEvent',
    'PullRequestEvent',
    'PushEvent',
    'CreateEvent',
    'CommitCommentEvent')
GROUP BY
  actor.login
ORDER BY cnt DESC
LIMIT
  180
```

