---
sidebar_position: 8
description: Ingest Dynatrace problems into your catalog
---

import DynatraceProblemBlueprint from "./resources/dynatrace/\_example_dynatrace_problem_blueprint.mdx";
import DynatraceProblemConfiguration from "./resources/dynatrace/\_example_dynatrace_problem_webhook_configuration.mdx"
import DynatraceMicroserviceBlueprint from "./resources/dynatrace/\_example_dynatrace_microservice_blueprint.mdx"

# Dynatrace

In this example you are going to create a webhook integration between [Dynatrace](https://www.dynatrace.com/) and Port, which will ingest problems entities to your microservices.

## Prerequisites

Create the following blueprint definitions and webhook configuration:

<details>
<summary>Dynatrace microservice blueprint</summary>
<DynatraceMicroserviceBlueprint/>
</details>

<details>
<summary>Dynatrace problem blueprint</summary>
<DynatraceProblemBlueprint/>
</details>

<details>
<summary>Dynatrace problem webhook configuration</summary>
<DynatraceProblemConfiguration/>
</details>

## Create the Dynatrace webhook

1. Log in to Dynatrace with your credentials;
2. Click on **Settings** at the left sidebar of the page;
3. Choose **Integration** and click on **Problem notifications**;
4. Select **Add notification**;
5. Select **Custom integration** from the available intregration types;
6. Input the following details:
   1. `Display name` - use a meaningful name such as Port Webhook;
   2. `Webhook URL` - enter the value of the `url` key you received after creating the webhook configuration;
   3. `Overview` - you can add an optional HTTP header to your webhook request;
   4. `Custom payload` - When a problem is detected or resolved on your entity, this payload will be sent to the webhook URL. You can enter this JSON placeholder in the textbox;
   ```json showLineNumbers
   {
   "State":"{State}",
   "ProblemID":"{ProblemID}",
   "ProblemTitle":"{ProblemTitle}",
   "ImpactedEntity": "{ImpactedEntity}",
   "ProblemDetailsText": "{ProblemDetailsText}",
   "ProblemImpact": "{ProblemImpact}",
   "ProblemSeverity": "{ProblemSeverity}",
   "ProblemURL": "{ProblemURL}",
   "ImpactedEntities": {ImpactedEntities}
   }
   ```
   5. `Alerting profile` - configure your preferred alerting rule or use the default one;
7. Click **Save changes** at the bottom of the page;

Done! any problem detected on your Dynatrace entity will trigger a webhook event. Port will parse the events according to the mapping and update the catalog entities accordingly.
