![License: CISCO](https://img.shields.io/badge/License-CISCO-blue.svg)
[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/<REPO-HERE>)

# Cisco SecureX orchestrator workflows to take action on OPENC2 command and controls

## Features
* Triggers based on webhook with OPENC2 command in request body;
* Parses OPENC2 command and takes action on: `deny`, `allow`, `contain` and `restore ` OPENC2 action types.
* Depending on OPENC2 target specific Cisco Security solutions are triggered:
  * `deny` and `allow` actions with `IPv4` or `IPv6` targets will trigger Firepower;
  * `deny` and `allow` actions with `domain` targets will trigger Umbrella;
  * `deny` and `allow` actions with `sha256` targets will trigger Cisco Secure Endpoint (AMP);
  * `contain` and `restore` actions with `IPv4` or `IPv6` targets will trigger Cisco Secure Endpoint (AMP) and/or Cisco Identity Services Engine;

## Roadmap
* Add `domain` support for Firepower;
* Add `IPv4` and `IPv6` support for Umbrella Cloud Delivered Firewall;
* Add `mac_address` and `hostname` support for Cisco Secure Endpoint (AMP) and/or Cisco Identity Services Engine;

> **Note:** Please test this properly before implementing in a production environment. This is a sample workflow!

## Required Targets
- CTR_For_Access_Token (default)
- CTR_API (default)
- Cisco Webex 
- Cisco Firepower Management Center
- Cisco Umbrella
- Cisco Secure Endpoint (AMP)
- Cisco Identity Services Engine

## Required Account Keys
- CTR_Credentials
- Webex Teams Token

## Required Global Variables
- Last Run Timestamp

## Required Atomic Workflows
- CTRGenerateAccessToken
- Webex Teams - Post Message to Room

## Setup instructions

### Configure Global Variables

1. Browse to your SecureX orchestration instance. This wille be a different URL depending on the region your account is in: 

* US: https://securex-ao.us.security.cisco.com/orch-ui/workflows/
* EU: https://securex-ao.eu.security.cisco.com/orch-ui/workflows/
* APJC: https://securex-ao.apjc.security.cisco.com/orch-ui/workflows/

2. In the left hand menu, select **Variables**.

3. Next steps.

### Import atomic actions

1. In the left pane menu, select **Workflows**. Click on **IMPORT** to import the workflow:

![](screenshots/import-workflow.png)

2. Click on **Browse** and copy paste the content of the [name-json-file.json](https://raw.githubusercontent.com/github-username/name-of-repo/master/name-json-file.json) file inside of the text window. Select **IMPORT AS A NEW WORKFLOW (CLONE)** and click on **IMPORT**.

![](screenshots/copy-paste.png)

### Import main workflow

1. In the left pane menu, select **Workflows**. Click on **IMPORT** to import the workflow.

2. Click on **Browse** and copy paste the content of the [name-json-file.json](https://raw.githubusercontent.com/github-username/name-of-repo/master/name-json-file.json) file inside of the text window.  Select **IMPORT AS A NEW WORKFLOW (CLONE)** and click on **IMPORT**.

3. Next steps, like updating targets / account keys and setting a trigger / running the workflow.

## Notes

* Please test this properly before implementing in a production environment. This is a sample workflow!
* In a future version capability X will be added. 

## Author(s)

* Name of Author (Cisco / Name of Company)
