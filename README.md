<a href="http://continuous.lu">
  <img src="https://app.continuousphp.com/assets/logos/continuousphp.svg" alt="ContinuousPHP" width="250px" align="right"/>
</a>

<p align="left">
  <a href="https://continuousphp.com/git-hub/continuousphp/cli"><img alt="Build Status" src="https://status.continuousphp.com/git-hub/continuousphp/cli?token=8eb1b41e-343a-41b5-b68f-179fb1ce1ffe&branch=master" /></a>
</p>

<p align="left">
    ContinuousPHP© is the first and only PHP-centric PaaS to build, package, test and deploy applications in the same workflow.
</p>

# ContinuousPHP\Notification-schema

Core:
  - BI
  - Pubnub
  - Github
  - Bitbucket
  - Gitlab

Optionnal:
  - SNS
  - SMS
  - Emails
  - IRC
  - Webhooks
  - HipChat
  - NewRelic
  - Scrutinizer-ci


## Event Types

  - build-start
  - activity-start
  - activity-end
  - build-fail
  - build-warning
  - build-success
  - build-deploy


## Notification Description Schema

```yaml
name: slack

core_events:
  - build-start
  - build-success

optional_events:
  - build-warning
  - build-deploy

attributes:
  - label: Slack WebHook URL
    key: url
    type: number|string
    required: bool
```


## Event Message Schema

```json
{
  event: 'build-start',
  build: {
    uid: '',
    provider: 'github',
    repository: 'ContinuousPHP/Foo',
    is_organization: true,
    builder: 'johndoe'
    pr_id: 157,
    refs: '/refs/heads/master',
    pipeline_id: '/refs/heads/*',
    commit: 'bc34514acabab234245124355652342353',
    status: 'success',
    commit_message: 'my feature commit',
    coverage: 0.8 // average of all test activity coverage,
    duration: seconds,
    start_time: DATETIME,
    activities: [{
      uid: '',
      type: 'package-test',
      name: 'Package test',
      start_time: DATETIME,
      end_time: DATETIME,
      state: 'finished',
      result: 'success',
      blocking: false,
      coverage: 0.8,
    }]
  }
}
```

