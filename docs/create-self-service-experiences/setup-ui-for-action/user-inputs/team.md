---
sidebar_position: 9
description: Team is an input used to reference teams that exist in Port
---

import ApiRef from "../../../api-reference/\_learn_more_reference.mdx"

import Tabs from "@theme/Tabs"
import TabItem from "@theme/TabItem"

# Team

Team is an input used to reference teams that exist in Port.

## 💡 Common team usage

The team input type can be used to reference any team that exists in Port, for example:

- The service owning team;
- The current on-call;
- The lead maintainers;
- etc.

In the [live demo](https://demo.getport.io/self-serve) self-service hub page, we can see the **scaffold new service** action whose `Owning Team` input is a user input. 🎬

## API definition

<Tabs groupId="api-definition" queryString defaultValue="basic" values={[
{label: "Basic", value: "basic"},
{label: "Array", value: "array"}
]}>

<TabItem value="basic">

```json showLineNumbers
{
  "myTeamInput": {
    "title": "My team input",
    "icon": "My icon",
    "description": "My team input",
    // highlight-start
    "type": "string",
    "format": "team",
    // highlight-end
    "default": "my-team"
  }
}
```

</TabItem>
<TabItem value="array">

```json showLineNumbers
{
  "myTeamArrayInput": {
    "title": "My team array input",
    "icon": "My icon",
    "description": "My team array input",
    // highlight-start
    "type": "array",
    "items": {
      "type": "string",
      "format": "team"
    }
    // highlight-end
  }
}
```

</TabItem>
</Tabs>

<ApiRef />

## Terraform definition

<Tabs groupId="tf-definition" queryString defaultValue="basic" values={[
{label: "Basic", value: "basic"},
{label: "Array - coming soon", value: "array"}
]}>

<TabItem value="basic">

```hcl showLineNumbers
resource "port-labs_action" "myAction" {
  # ...action properties
  # highlight-start
  user_properties {
    identifier  = "myTeamInput"
    title       = "My team input"
    description = "My team input"
    required    = false
    type        = "string"
    format      = "team"
    default     = "my-team"
  }
  # highlight-end
}
```

</TabItem>
</Tabs>
