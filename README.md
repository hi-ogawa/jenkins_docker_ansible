Assume target server is running on Ubuntu Server 14.04 (ami-a21529cc)

```
$ ansible --version
ansible 2.1.0 (devel 50dfd4b057) last updated 2016/02/07 13:39:55 (GMT +900)
  lib/ansible/modules/core: (detached HEAD e1ec52e365) last updated 2016/02/07 13:41:53 (GMT +900)
  lib/ansible/modules/extras: (detached HEAD 14a62fb5d6) last updated 2016/02/07 13:42:45 (GMT +900)
  config file =
  configured module search path = Default w/o overrides

$ ansible -i hosts -l production all -m ping
$ ansible-playbook -i hosts -l production playbook.yml
```

### Manual Configuration

- Plugins:
  - github
  - embeddable-build-status

- Manage security:
  - disable signup
  - jenkins' own user database
  - matrix-based security
    - for anonymous: Overall:Read, Job:Read

- Create user: http://jenkins.hiogawa.net/securityRealm/addUser

- Configure "Jenkins (GitHub plugin)" on github (e.g. https://github.com/username/reponame/settings/hooks/)

- Setup slack integration https://slack.com/apps/A0F7VRFKN-jenkins-ci

- Create project:
  - click `New Item`
  - input `Item name` and choose `Freestyle project`
  - choose `GitHub project` and input `Project url`
  - choose `Git` under `Source Code Management`, input `Repository URL`
    - use `https://` instead of `git@` to clone public gihub repoisitory without setting up deploy key
  - choose `Build when a change is pushed to GitHub` under `Build Triggers`
  - choose `Execute shell` under `Build` and input shell script to run tests
  - choose `Slack Notifications` under `Post-build Actions`


### References

- https://github.com/dochang/ansible-role-docker
