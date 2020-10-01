# CDF Hacktoberfest Information
Information and guidelines for participating in the CDF's Hacktoberfest program

## How To Sign Up
Participating in CDF Hacktoberfest is simple. Visit our [check-in form](https://rb.gy/lxfhco) to sign up and be added to the leaderboard. When you sign up, you'll indicate whether or not you want to receive swag prizes if you're among the top 10 contributors from your project. 

Once you're checked in, start contributing! Whether or not you want to receive swag, we will recognize and celebrate your contributions.

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

This will facilitate easy tracking and review of all contributions from the participating CDF community. All participants will be added to the [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest) organization after checking in to the event and providing a GitHub username on the [check-in form](https://rb.gy/lxfhco).

## Points Eligibility

The CDF Project Outreach team will track and tally points based on GitHub activity in eligible organizations, and other eligible content contributions as tracked in the [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest) organization and in the [#hacktoberfest channel](https://cdeliveryfdn.slack.com/archives/C01BRCQ7RJN) on [CDF Slack](https://join.slack.com/t/cdeliveryfdn/shared_invite/zt-ao8y4qhd-BQcTUg5l7m0HxXyBvJrT4w).

Eligible GitHub events include __pull request creation__, __commiting__, __issue creation__, and __issue and pull request commenting__ in CDF project repositories. Those event types, along with __pushing__ and __repository creation__ will be tallied where contributors can perform those events, in less restricted hack respositories such as [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest).

Eligible content contributions include, but are not limited to __blog posts__, __videos__, __Twitch streams__, __training guides__, __stackoverflow answers__, and __whitepapers__. To submit your content for points eligibility, do the following:
1. If possible, initiate it in a respository in the [cdf-hacktoberfest](https://github.com/cdf-hacktoberfest) organization. 
2. Once content is published in its public destination, take a clear screenshot of it.
3. Post a message about your contribution in the [#hacktoberfest channel](https://cdeliveryfdn.slack.com/archives/C01BRCQ7RJN) on [CDF Slack](https://join.slack.com/t/cdeliveryfdn/shared_invite/zt-ao8y4qhd-BQcTUg5l7m0HxXyBvJrT4w). Your message should include:
    - Screenshot
    - Your GitHub username
    - A brief description of the content  
4. After you post your message, add a :hacktoberfest: emoji reaction to your message. _Your points will not be counted unless you add this reaction_. If needed, [learn how to use reactions in Slack](https://slack.com/help/articles/206870317-Use-emoji-reactions). 

## Leaderboard and Points Tracking

Use the [CDF Hacktoberfest Leaderboard](https://rb.gy/0cya5p) to track your contribution totals, noting the time delay detailed below. We will use the following query against the [GH Archive dataset of public GitHub activity](https://www.gharchive.org/) to track contributions according to organization name:

```
SELECT
  actor.login,
  COUNT(*) as cnt,
FROM
  `githubarchive.month.*`
WHERE
  (repo.name LIKE 'spinnaker/%' OR  repo.name LIKE 'spinnaker-hackathon/%' OR repo.name LIKE 'jenkinsci/%' OR repo.name LIKE 'jenkins-infra/%' OR repo.name LIKE 'jenkins-zh/%' OR repo.name LIKE 'tektoncd/%' OR repo.name LIKE 'jenkins-x/%' OR repo.name LIKE 'screwdriver-cd/%' OR repo.name LIKE 'cdf-hacktoberfest/%')
  AND created_at >= '2020-9-30 12:00:00'
  AND created_at < '2020-11-01 12:00:00'
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
Note: Our leaderboard on Google Sheets uses BigQuery to grab this data. This archive is a great way to get it, but there is a lag in the way the data is aggregated from GitHub APIs and aggregated into the archive. There is typically a 24-hour lag in the reflection of GitHub events in the archive, but it can sometimes be longer than 24 hours depending on what time the contribution was made. Therefore, __there will be a delay__ in the visualization of your contributions.

## Prizes

At the end of Hacktoberfest (after October 31), we will reward the top 4 contributors in each of the 5 CDF projects with awesome gear from the CDF swag store. If 4 contributors are not registered from each project, folks with the next highest points totals from active projects will receive prizes until we have rewarded 20 contributors. If you want to participate and be recognized, but prefer not to receive swag, you may indicate that when you check in to CDF Hacktoberfest using the [check-in form](https://rb.gy/lxfhco).

