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

The CDF Project Outreach team will track and tally points based on GitHub activity in eligible organizations, and other eligible content contributions as tracked in the [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest) organization and in [Slack](link-to-Slack-channel).

Eligible GitHub events include __pull request creation__, __commiting__, __issue creation__, and __issue and pull request commenting__ in CDF project repositories. Those event types, along with __pushing__ and __repository creation__ will be tallied where contributors can perform those events, in less restricted hack respositories such as [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest).

Eligible content contributions include, but are not limited to __blog posts__, __videos__, __Twitch streams__, __training guides__, __stackoverflow answers__, and __whitepapers__. To submit your content for points eligibility, initiate it in a respository in the [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest) organization if possible. Once content is published or posted in its public destination, post a clear screenshot of it along with your GitHub username in the [Slack channel name](slack-url.com).

We will use the following query against the [GH Archive dataset of public GitHub activity](https://www.gharchive.org/) to track contributions according to organization name:

```
SELECT
  actor.login,
  COUNT(*) as cnt,
FROM
  `githubarchive.month.*`
WHERE
  (repo.name LIKE 'spinnaker/%' OR  repo.name LIKE 'spinnaker-hackathon/%' OR repo.name LIKE 'jenkinsci/%' OR repo.name LIKE 'jenkins-x/%' OR repo.name LIKE 'screwdriver-cd/%' OR repo.name LIKE 'tektoncd/%' OR repo.name LIKE 'cdf-hacktoberfest/%')
  AND created_at >= '2020-10-01 00:00:00'
  AND created_at < '2020-11-01 00:00:00'
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
Our leaderboard on Google Sheets uses BigQuery to grab this data. This archive is a great way to get it, but there is a lag in the way the data is aggregated from GitHub APIs and aggregated into the archive. There is typically a 24-hour lag in the reflection of GitHub events in the archive, but it can sometimes be longer than 24 hours depending on what time the contribution was made. Therefore, __there will be a delay__ in the visualization of your contributions.
