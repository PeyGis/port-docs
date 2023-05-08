---
sidebar_position: 1
description: Text is a basic input for textual information
---

import ApiRef from "../../../api-reference/\_learn_more_reference.mdx"

import Tabs from "@theme/Tabs"
import TabItem from "@theme/TabItem"

# Text

Text is a basic input for textual information.

## 💡 Common text usage

The text input type can be used to store any text based data, for example:

- Image tags;
- Variable keys;
- Commit SHA;
- File names;
- etc.

In the [live demo](https://demo.getport.io/self-serve) self-service hub page, we can see the **scaffold new service** action whose `Service Name` input is a text input. 🎬

## API definition

<Tabs groupId="api-definition" queryString defaultValue="basic" values={[
{label: "Basic", value: "basic"},
{label: "Select (Enum)", value: "enum"},
{label: "Array", value: "array"}
]}>

<TabItem value="basic">

```json showLineNumbers
{
  "myTextInput": {
    "title": "My text input",
    "icon": "My icon",
    "description": "My text input",
    // highlight-start
    "type": "string",
    // highlight-end
    "default": "My default"
  }
}
```

</TabItem>
<TabItem value="enum">

```json showLineNumbers
{
  "myTextSelectInput": {
    "title": "My text select input",
    "icon": "My icon",
    "description": "My text select input",
    "type": "string",
    // highlight-next-line
    "enum": ["my-option-1", "my-option-2"]
  }
}
```

</TabItem>
<TabItem value="array">

```json showLineNumbers
{
  "myTextArrayInput": {
    "title": "My text array input",
    "icon": "My icon",
    "description": "My text array input",
    // highlight-start
    "type": "array",
    "items": {
      "type": "string"
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
    identifier  = "myTextInput"
    title       = "My text input"
    description = "My text input"
    required    = false
    type        = "string"
    default     = "My default"
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
    identifier  = "myTextSelectInput"
    title       = "My text Select input"
    description = "My text select input"
    required    = false
    type        = "string"
    enum        = ["my-option-1", "my-option-2"]
  }
  # highlight-end
}

```

</TabItem>
</Tabs>

## Validate text

Text validations support the following operators:

- `minLength` - enforce minimal string length;
- `maxLength` - enforce maximal string length;
- `pattern` - enforce Regex patterns.

<Tabs groupId="validation-definition" queryString defaultValue="basic" values={[
{label: "Basic", value: "basic"},
{label: "Array", value: "array"},
{label: "Terraform - coming soon", value: "tf"}
]}>

<TabItem value="basic">

```json showLineNumbers
{
  "myTextInput": {
    "title": "My text input",
    "icon": "My icon",
    "description": "My text input",
    "type": "string",
    // highlight-start
    "minLength": 1,
    "maxLength": 32,
    "pattern": "^[a-zA-Z0-9-]*-service$"
    // highlight-end
  }
}
```

</TabItem>

<TabItem value="array">

```json showLineNumbers
{
  "myTextArrayInput": {
    "title": "My text array input",
    "icon": "My icon",
    "description": "My text array input",
    // highlight-start
    "type": "array",
    "items": {
      "type": "string",
      "minLength": 1,
      "maxLength": 32,
      "pattern": "^[a-zA-Z0-9-]*-service$"
    }
    // highlight-end
  }
}
```

</TabItem>
</Tabs>
