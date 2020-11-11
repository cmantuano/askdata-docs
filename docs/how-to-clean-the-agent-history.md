---
title: How to clean the agent history
keywords: documentation
last_updated: November 11th, 2020
tags: [getting_started]
sidebar: mydoc_sidebar
layout: docs
---

In order to clean the agent history for your user you can run the following **shell commands:**

**1. Shell: Get User Token**

```shell
curl --location --request POST 'https://security.askdata.com/domain/{{domain}}/oauth/token' \
--header 'Authorization: Basic ZmVlZDpmZWVk' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'cache-control: no-cache' \
--data-urlencode 'grant_type=password' \
--data-urlencode 'username={{username}}' \
--data-urlencode 'password={{pwd}}'
```

**2. Locate your agent slug**

You can locate your agent slug from the home of your agent

<img src="media/workspace_how_to_find_slug.png" style="max-wdith:400px" />

**3. Shell: Get AgentId from Agent Slug**

```shell
curl --location --request GET 'https://smartbot.askdata.com/agents/agentslug/{{slug}}'
```

**4. Shell: Clear Message History**

```shell
curl --location --request DELETE 'https://smartfeed.askdata.com/{{domain}}/agent?agentId={{agentId}}' \
--header 'Authorization: Bearer {{token}}' \
--header 'Content-Type: application/json'
```

**Standard Variables:**

domain: askdata


{% include links.html %}
