Assignment 6:
"Create a Ansible shared library in Jenkins for your tool with following steps:
- clone
- User Approval
- Playbook Execution
- Notification
Required inputs for the shared library should be passed via configuration file
eg:
SLACK_CHANNEL_NAME  = build-status
ENVIRONMENT         = prod
CODE_BASE_PATH      = env/prod
ACTION_MESSAGE      = <channel message>
KEEP_APPROVAL_STAGE = "true"
