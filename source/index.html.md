---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://cloud.aha.volenday.com/'>Sign Up for a API Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

#includes:
#  - errors

search: true
---

# Introduction

> Install the AHA SDK

```shell
#npm
npm install @volenday/sdk --save

#yarn
yarn add @volenday/sdk
```

Welcome to the AHA! You can use our API to access AHA API endpoints, which can get be use for you AHA applications.

Currently, we support REST API and Node.js SDK.

# Initialization

> Initialize your app by passing the api key

```javascript
import { ENVIRONMENTS, initialize } from "@volenday/sdk";

initialize({ apiKey: "API_KEY", environment: ENVIRONMENTS.SANDBOX });
```

> Make sure to replace `API_KEY` with your API key.

Start by initializing your application.

### Parameters

| Key         | Required | Default    | Description                                                                                    |
| ----------- | -------- | ---------- | ---------------------------------------------------------------------------------------------- |
| apiKey      | true     | -          | Can be get/created in you AHA cloud account.                                                   |
| environment | true     | production | You can set it to sandbox by using the SDK ENVIRONMENTS and call it like ENVIRONMENTS.SANDBOX. |

Please take note that you only need initialize you app once in your root file.

<aside class="notice">
Make sure to replace <code>API_KEY</code> with your API key.
</aside>
