Slack.io status plugin for Buildbot
===================================

This Buildbot plugin sends messages to a Slack.io channel when each build finishes with a handy link to the build results.

This plugin is based on the buildbot-status-hipchat plugin created by the dev team at http://www.pricingassistant.com/ ; Contributions are welcome!

## Install

### via pip

```
pip install -e git+https://github.com/mindmatters/buildbot-status-slack#egg=slack
```

### manual

Copy slack.py next to your master.cfg file


## Setup

Create a new Incomming Webhook in your slack account.

Then in your master.cfg, add the following:

```
import slack
c['status'].append(slack.SlackStatusPush("YOUR_SLACK_WEBURL"))
```

### Additional Options:
```
  localhost_replace = False
  username = None
  icons = None
  notify_on_success = True
  notify_on_failure = True
  builders = None
```

### Complete Example:

```
import slack
slack_status = slack.SlackStatusPush(
    "YOUR_SLACK_WEBURL",
    localhost_replace="http://ci.mindmatters.de",
    username="mindmatters Buildbot",
    icons=(':full_moon_with_face:', ':umbrella:'),
    notify_on_success=False,
    notify_on_failure=True,
)
c['status'].append(slack_status)
```

Enjoy!

