---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://cloud.aha.volenday.com/auth/sign-up'>Sign Up for a API Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

#includes:
#  - errors

search: false
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

# Database

## GET / FETCH

To get the list of recrods or specific record by id, you have to use the get function under database object. You can narrow your query by using the chain methods.

```javascript
const { database } = require("@volenday/sdk");

database
  .get({
    entity: "ENTITY_ID",
    environment: ENVIRONMENTS.SANDBOX,
    token: "ACCESS_TOKEN"
  })
  .all()
  .autoPopulate(true)
  .count()
  .fields(["FirstName", "LastName"])
  .filter({ Age: { $gte: 18 } })
  .ids([1, 2, 3])
  .keywords("John Doe")
  .page(1)
  .populate(["UserTypes"])
  .setId(1)
  .size(50)
  .sort({ FirstName: 1 })
  .exec()
  .then(function(response) {})
  .catch(function(error) {});

//ES2015 / ES6
import { database } from "@volenday/sdk";

const response = await database
  .get({
    entity: "ENTITY_ID",
    environment: ENVIRONMENTS.SANDBOX,
    token: "ACCESS_TOKEN"
  })
  .all()
  .autoPopulate(true)
  .count()
  .fields(["FirstName", "LastName"])
  .filter({ Age: { $gte: 18 } })
  .ids([1, 2, 3])
  .keywords("John Doe")
  .page(1)
  .populate(["UserTypes"])
  .setId(1)
  .size(50)
  .sort({ FirstName: 1 })
  .exec();
```

> Make sure to replace all necessary parameters.

### Parameters

| Key         | Required | Default                                       | Description                            |
| ----------- | -------- | --------------------------------------------- | -------------------------------------- |
| entity      | true     | -                                             | Entity/Table/Collection ID             |
| token       | true     | Autoset from initialize function (production) | Access or ID token from authentication |
| environment | true     | Autoset from initialize function (production) | Either sandbox or production           |

### Methods

| Key          | Required | Default      | Description                                                                     |
| ------------ | -------- | ------------ | ------------------------------------------------------------------------------- |
| exec         | true     |              | To execute the whole chain                                                      |
| all          | false    | false        | To get all records and disregard the pagination                                 |
| autoPopulate | false    | true         | This will auto populate all reference connected entity                          |
| count        | false    | false        | To get records count                                                            |
| fields       | false    | [all fields] | To specify which fields you want return                                         |
| filter       | false    | {}           | This method is using all mongodb querying methods like $eq, $gt/$gte, $lt/\$lte |
| ids          | false    | []           | To filter specific list of records IDs                                          |
| keywords     | false    | ''           | If you need to filter all string fields by string of text                       |
| page         | false    | 1            | Will be use for pagination                                                      |
| populate     | false    | []           | Incase autoPopulate is off and you want to populate specific fields only        |
| setId        | false    | -            | This is to get 1 record                                                         |
| size         | false    | 50           | Number of records to return                                                     |
| sort         | false    | {Id: -1}     | Sort the return records, 1 for ASC and -1 for DESC                              |

<aside class="notice">
Make sure to replace all necessary parameters.
</aside>

## CREATE

Create or add new record to your entity, this accepts a javascript object. Incase you have file fields in you entity, SDK will automatically do form-data transfer.

```javascript
const { database } = require("@volenday/sdk");

database
  .create({
    entity: "ENTITY_ID",
    environment: ENVIRONMENTS.SANDBOX,
    token: "ACCESS_TOKEN"
  })
  .autoPopulate(true)
  .data({ FirstName: "John", LastName: "Doe" })
  .populate(["UserTypes"])
  .exec()
  .then(function(response) {})
  .catch(function(error) {});

//ES2015 / ES6
import { database } from "@volenday/sdk";

const response = await database
  .create({
    entity: "ENTITY_ID",
    environment: ENVIRONMENTS.SANDBOX,
    token: "ACCESS_TOKEN"
  })
  .autoPopulate(true)
  .data({ FirstName: "John", LastName: "Doe" })
  .populate(["UserTypes"])
  .exec();
```

> Make sure to replace all necessary parameters.

### Parameters

| Key         | Required | Default                                       | Description                            |
| ----------- | -------- | --------------------------------------------- | -------------------------------------- |
| entity      | true     | -                                             | Entity/Table/Collection ID             |
| token       | true     | Autoset from initialize function (production) | Access or ID token from authentication |
| environment | true     | Autoset from initialize function (production) | Either sandbox or production           |

### Methods

| Key          | Required | Default | Description                                                              |
| ------------ | -------- | ------- | ------------------------------------------------------------------------ |
| exec         | true     |         | To execute the whole chain                                               |
| autoPopulate | false    | true    | This will auto populate all reference connected entity                   |
| data         | true     | {}      | Javascript object containing the form data                               |
| populate     | false    | []      | Incase autoPopulate is off and you want to populate specific fields only |

<aside class="notice">
Make sure to replace all necessary parameters.
</aside>

## UPDATE / PATCH

Update a record to your entity, this accepts a javascript object. Pass only the fields you want to update

```javascript
const { database } = require("@volenday/sdk");

database
  .update({
    entity: "ENTITY_ID",
    environment: ENVIRONMENTS.SANDBOX,
    id: "RECORD_ID",
    token: "ACCESS_TOKEN"
  })
  .autoPopulate(true)
  .data({ FirstName: "John" })
  .populate(["UserTypes"])
  .exec()
  .then(function(response) {})
  .catch(function(error) {});

//ES2015 / ES6
import { database } from "@volenday/sdk";

const response = await database
  .update({
    entity: "ENTITY_ID",
    environment: ENVIRONMENTS.SANDBOX,
    id: "RECORD_ID",
    token: "ACCESS_TOKEN"
  })
  .autoPopulate(true)
  .data({ FirstName: "John" })
  .populate(["UserTypes"])
  .exec();
```

> Make sure to replace all necessary parameters.

### Parameters

| Key         | Required | Default                                       | Description                            |
| ----------- | -------- | --------------------------------------------- | -------------------------------------- |
| entity      | true     | -                                             | Entity/Table/Collection ID             |
| token       | true     | Autoset from initialize function (production) | Access or ID token from authentication |
| id          | true     | -                                             | Record ID to update                    |
| environment | true     | Autoset from initialize function (production) | Either sandbox or production           |

### Methods

| Key          | Required | Default | Description                                                              |
| ------------ | -------- | ------- | ------------------------------------------------------------------------ |
| exec         | true     |         | To execute the whole chain                                               |
| autoPopulate | false    | true    | This will auto populate all reference connected entity                   |
| data         | true     | {}      | Javascript object containing the form data                               |
| populate     | false    | []      | Incase autoPopulate is off and you want to populate specific fields only |

<aside class="notice">
Make sure to replace all necessary parameters.
</aside>

## DELETE

Delete a record to your entity.

```javascript
const { database } = require("@volenday/sdk");

database
  .delete({
    entity: "ENTITY_ID",
    environment: ENVIRONMENTS.SANDBOX,
    id: "RECORD_ID",
    token: "ACCESS_TOKEN"
  })
  .exec()
  .then(function(response) {})
  .catch(function(error) {});

//ES2015 / ES6
import { database } from "@volenday/sdk";

const response = await database
  .delete({
    entity: "ENTITY_ID",
    environment: ENVIRONMENTS.SANDBOX,
    id: "RECORD_ID",
    token: "ACCESS_TOKEN"
  })
  .exec();
```

> Make sure to replace all necessary parameters.

### Parameters

| Key         | Required | Default                                       | Description                            |
| ----------- | -------- | --------------------------------------------- | -------------------------------------- |
| entity      | true     | -                                             | Entity/Table/Collection ID             |
| token       | true     | Autoset from initialize function (production) | Access or ID token from authentication |
| id          | true     | -                                             | Record ID to update                    |
| environment | true     | Autoset from initialize function (production) | Either sandbox or production           |

### Methods

| Key  | Required | Default | Description                |
| ---- | -------- | ------- | -------------------------- |
| exec | true     |         | To execute the whole chain |

<aside class="notice">
Make sure to replace all necessary parameters.
</aside>
