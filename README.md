# Back-End Solution to Report Voice "Hang Up By" in Flex Insights

This is a minimal back-end solution to populating "Hang Up By" data in **Twilio Flex Insights**.

This solution will only track if the Conference was ended by the `customer` or the `agent`. 

> [!TIP]
> For a slightly enhanced solution which logs `customer`, `agent`, or the unexpected `disconnect`, check out [this other minimal approach](https://github.com/brypo/flex-insights-hang-up-by/tree/main).
> 
> For a very enhanced solution, consider the [Twilio's Flex Project Template - Hang Up By](https://twilio-professional-services.github.io/flex-project-template/feature-library/hang-up-by) implementation.

## How does this work?
This solution uses the [TaskRouter Workspace Callback Event URL](https://www.twilio.com/docs/taskrouter/api/event/reference#:~:text=TaskRouter%20will%20make,Event%20takes%20place.) and points it to a [Twilio Serverless Function](https://www.twilio.com/docs/serverless/functions-assets/functions). This Function listens for the `task.wrapup` event from TaskRouter, and if it is a "voice" Task, it will check to see who ended the Conference and update Flex Insights with either `customer` or `agent`.

## Environment Variables
| Variable | Example Identifier |
| ----- | ---- |
| `WORKSPACE_SID` | WSxxxxxxxxxx

## Disclaimer
This software is to be considered "sample code", a Type B Deliverable, and is delivered "as-is" to the user. Twilio bears no responsibility to support the use or implementation of this software.
