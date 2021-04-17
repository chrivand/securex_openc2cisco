![License: CISCO](https://img.shields.io/badge/License-CISCO-blue.svg)
[![published](https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg)](https://developer.cisco.com/codeexchange/github/repo/<REPO-HERE>)

# Cisco SecureX orchestrator workflows to take action on OpenC2 command and controls ("OpenC2Cisco" or "OC2C")
This is a set of SecureX orchestrator workflows to take action on [OPENC2 command and controls](https://docs.oasis-open.org/openc2/oc2ls/v1.0/cs02/oc2ls-v1.0-cs02.html). Please check the [following slidedeck](https://github.com/chrivand/securex_openc2cisco/blob/main/openc2cisco.pdf) for more information regarding the flow of the solution.

## Features
* Triggers based on webhook with OPENC2 command in request body;
* Parses OPENC2 command and takes action on: `deny`, `allow`, `contain` and `restore` OPENC2 action types;
* Depending on OPENC2 target specific Cisco Security solutions are triggered:
  * `deny` and `allow` actions with `IPv4` or `IPv6` targets will trigger Cisco Secure Firewall (Firepower);
  * `deny` and `allow` actions with `domain` targets will trigger Cisco Umbrella;
  * `deny` and `allow` actions with `sha256` targets will trigger Cisco Secure Endpoint (AMP);
  * `contain` and `restore` actions with `IPv4` or `IPv6` targets will trigger Cisco Secure Endpoint (AMP) and/or Cisco Identity Services Engine.
* Uses [Hashicorp Vault](https://www.vaultproject.io/) to retrieve API keys for various Cisco solutions;
* Creates Webex alerts messages for Security Operations Center (SOC) or other help desk;
* Creates case in SecureX Casebook for Security Operations Center (SOC) or other help desk.

## Roadmap
* Add `query` action support for Cisco Identity Services Engine and Microsoft Active Directory;
* Add `domain` target support for Cisco Secure Firewall (Firepower);
* Add `IPv4` and `IPv6` target support for Umbrella Cloud Delivered Firewall;
* Add `mac_address` and `hostname` target support for Cisco Secure Endpoint (AMP) and/or Cisco Identity Services Engine;
* More to be announced...

> **Note:** Please test this properly before implementing in a production environment. This is a sample workflow!

## Required Targets
- CTR_For_Access_Token (default)
- CTR_API (default)
- Cisco Webex 
- Cisco Secure Firewall (Firepower) [REMOTE CONNECTOR NEEDED]
- Cisco Umbrella
- Cisco Secure Endpoint (AMP)
- Hashicorp Vault

## Required Account Keys
- Depends on using Vault or not, but at minimum Vault keys, and otherwise keys for all targets.

## Required Atomic Workflows
- Threat Response v2 - Generate Access Token
- Threat Response v2 - Create Casebook
- Webex Teams - Post Message to Room
- FMC - Get Access Tokens
- [AMP_add_to_block_list.json](https://raw.githubusercontent.com/chrivand/securex_openc2cisco/main/atomics/AMP_add_to_block_list.json)
- [fmc_update_dynamic_object.json](https://raw.githubusercontent.com/chrivand/securex_openc2cisco/main/atomics/fmc_update_dynamic_object.json)
- [hashicorp_vault_read_keys.json](https://raw.githubusercontent.com/chrivand/securex_openc2cisco/main/atomics/hashicorp_vault_read_keys.json)
- [openc2_parser.json](https://raw.githubusercontent.com/chrivand/securex_openc2cisco/main/atomics/openc2_parser.json)
- [umbrella_add_to_enforcement_block_list.json](https://raw.githubusercontent.com/chrivand/securex_openc2cisco/main/atomics/umbrella_add_to_enforcement_block_list.json)

## Setup instructions

### Import atomic actions

1. In the left pane menu, select **Workflows**. Click on **IMPORT** to import the workflow:

![](screenshots/import-workflow.png)

2. Click on **Browse** and copy paste the content of the [atomics](https://github.com/chrivand/securex_openc2cisco/tree/main/atomics) files inside of the text window (one by one). Select **IMPORT AS A NEW WORKFLOW (CLONE)** and click on **IMPORT**.

![](screenshots/copy-paste.png)

### Import main workflow

1. In the left pane menu, select **Workflows**. Click on **IMPORT** to import the workflow.

2. Click on **Browse** and copy paste the content of the [main_workflow.json](https://raw.githubusercontent.com/chrivand/securex_openc2cisco/main/main_workflow.json) file inside of the text window.  Select **IMPORT AS A NEW WORKFLOW (CLONE)** and click on **IMPORT**.

3. Now you will need to make sure that you have all required targets and account keys. If you are using vault, you can easily retrieve them using the "Read Vault Secrets" atomic action and then reference them later.

## Notes

* Please test this properly before implementing in a production environment. This is a sample workflow!

## Author(s)

* Kareem Iskander (Cisco)
* Krishan Veer (Cisco)
* Pieter van Schaik (Cisco)
* Christopher van der Made (Cisco)
