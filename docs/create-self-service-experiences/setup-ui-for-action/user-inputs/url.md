---
sidebar_position: 6
description: URL is an input used to save links to websites
---

import ApiRef from "../../../api-reference/\_learn_more_reference.mdx"

import Tabs from "@theme/Tabs"
import TabItem from "@theme/TabItem"

# URL

URL is an input used to save links to websites.

## 💡 Common url usage

The URL input type can be used to store a link to any web resource, for example:

- Link to Datadog dashboard;
- Link to configuration file;
- Link to pull request;
- etc.

## API definition

<Tabs groupId="api-definition" queryString defaultValue="basic" values={[
{label: "Basic", value: "basic"},
{label: "Select (Enum)", value: "enum"},
{label: "Array", value: "array"}
]}>

<TabItem value="basic">

```json showLineNumbers
{
  "myUrlInput": {
    "title": "My url input",
    "icon": "My icon",
    "description": "My url input",
    // highlight-start
    "type": "string",
    "format": "url",
    // highlight-end
    "default": "https://example.com"
  }
}
```

</TabItem>
<TabItem value="enum">

```json showLineNumbers
{
  "myUrlSelectInput": {
    "title": "My url select input",
    "icon": "My icon",
    "description": "My url select input",
    "type": "string",
    "format": "url",
    // highlight-next-line
    "enum": ["https://example.com", "https://getport.io"]
  }
}
```

</TabItem>
<TabItem value="array">

```json showLineNumbers
{
  "myUrlArrayInput": {
    "title": "My url array input",
    "icon": "My icon",
    "description": "My url array input",
    // highlight-start
    "type": "array",
    "items": {
      "type": "string",
      "format": "url"
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
{label: "Select (Enum)", value: "enum"},
{label: "Array - coming soon", value: "array"}
]}>

<TabItem value="basic">

```hcl showLineNumbers
resource "port-labs_action" "myAction" {
  # ...action properties
  # highlight-start
  user_properties {
    identifier  = "myUrlInput"
    title       = "My url input"
    description = "My url input"
    required    = false
    type        = "string"
    format      = "url"
    default     = "https://example.com"
  }
  # highlight-end
}
```

</TabItem>

<TabItem value="enum">

```hcl showLineNumbers
resource "port-labs_action" "myAction" {
  # ...action properties
  # highlight-start
  user_properties {
    identifier  = "myUrlSelectInput"
    title       = "My url select input"
    description = "My url select input"
    required    = false
    type        = "string"
    format      = "url"
    enum        = ["https://example.com", "https://getport.io"]
  }
  # highlight-end
}
```

</TabItem>
</Tabs>
