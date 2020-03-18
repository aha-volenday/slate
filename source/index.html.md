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
const { ENVIRONMENTS, initialize } = require("@volenday/sdk");

//ES2015 / ES6
import { ENVIRONMENTS, initialize } from "@volenday/sdk";

initialize({ apiKey: "API_KEY", environment: ENVIRONMENTS.SANDBOX });
```

> Make sure to replace all necessary parameters.

Start by initializing your application.

### Parameters

| Key         | Required | Default    | Description                                                                                    |
| ----------- | -------- | ---------- | ---------------------------------------------------------------------------------------------- |
| apiKey      | true     | -          | Can be get/created in you AHA cloud account.                                                   |
| environment | true     | production | You can set it to sandbox by using the SDK ENVIRONMENTS and call it like ENVIRONMENTS.SANDBOX. |

Please take note that you only need initialize you app once in your root file.

<aside class="notice">
Make sure to replace all necessary parameters.
</aside>

# Authentication

## Login with Email Address

```javascript
const { auth } = require("@volenday/sdk");

auth
  .loginWithEmail({
    apiKey: "API_KEY",
    emailAddress: "USER_EMAIL",
    environment: ENVIRONMENTS.SANDBOX,
    headers: {},
    password: "USER_PASSWORD",
    rememberMe: false
  })
  .then(function(response) {})
  .catch(function(error) {});

//ES2015 / ES6
import { auth } from "@volenday/sdk";

const response = await auth.loginWithEmail({
  apiKey: "API_KEY",
  emailAddress: "USER_EMAIL",
  environment: ENVIRONMENTS.SANDBOX,
  headers: {},
  password: "USER_PASSWORD",
  rememberMe: false
});
```

> Make sure to replace all necessary parameters.

### Parameters

| Key          | Required | Default                                       | Description                                 |
| ------------ | -------- | --------------------------------------------- | ------------------------------------------- |
| apiKey       | true     | Autoset from initialize function              | Can be get/created in you AHA cloud account |
| emailAddress | true     | -                                             | Email Address                               |
| password     | true     | -                                             | Password                                    |
| environment  | false    | Autoset from initialize function (production) | Either sandbox or production                |
| headers      | false    | {'Content-Type':'application/json'}           | Pass your custom headers                    |
| rememberMe   | false    | false                                         | To disregard the session timeout            |

## Login with Google

You have to handle the google popup login or oauth. On login success, google will provide an access token or id token. You have to pass that token to AHA SDK.

```javascript
const { auth } = require("@volenday/sdk");

auth
  .loginWithGoogle({
    apiKey: "API_KEY",
    environment: ENVIRONMENTS.SANDBOX,
    headers: {},
    token: "ACCESS_TOKEN"
  })
  .then(function(response) {})
  .catch(function(error) {});

//ES2015 / ES6
import { auth } from "@volenday/sdk";

const response = await auth.loginWithGoogle({
  apiKey: "API_KEY",
  environment: ENVIRONMENTS.SANDBOX,
  headers: {},
  token: "ACCESS_TOKEN"
});
```

> Make sure to replace all necessary parameters.

### Parameters

| Key         | Required | Default                                       | Description                                 |
| ----------- | -------- | --------------------------------------------- | ------------------------------------------- |
| apiKey      | true     | Autoset from initialize function              | Can be get/created in you AHA cloud account |
| token       | true     | -                                             | Access or ID token from google login        |
| environment | false    | Autoset from initialize function (production) | Either sandbox or production                |
| headers     | false    | {'Content-Type':'application/json'}           | Pass your custom headers                    |

<aside class="notice">
Make sure to replace all necessary parameters.
</aside>

## Login with Facebook

You have to handle the facebook popup login or oauth. On login success, facebook will provide an access token or id token. You have to pass that token to AHA SDK.

```javascript
const { auth } = require("@volenday/sdk");

auth
  .loginWithFacebook({
    apiKey: "API_KEY",
    environment: ENVIRONMENTS.SANDBOX,
    headers: {},
    token: "ACCESS_TOKEN"
  })
  .then(function(response) {})
  .catch(function(error) {});

//ES2015 / ES6
import { auth } from "@volenday/sdk";

const response = await auth.loginWithFacebook({
  apiKey: "API_KEY",
  environment: ENVIRONMENTS.SANDBOX,
  headers: {},
  token: "ACCESS_TOKEN"
});
```

> Make sure to replace all necessary parameters.

### Parameters

| Key         | Required | Default                                       | Description                                 |
| ----------- | -------- | --------------------------------------------- | ------------------------------------------- |
| apiKey      | true     | Autoset from initialize function              | Can be get/created in you AHA cloud account |
| token       | true     | -                                             | Access or ID token from facebook login      |
| environment | false    | Autoset from initialize function (production) | Either sandbox or production                |
| headers     | false    | {'Content-Type':'application/json'}           | Pass your custom headers                    |

<aside class="notice">
Make sure to replace all necessary parameters.
</aside>
