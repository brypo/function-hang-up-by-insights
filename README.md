# Back-End Solution to Report Voice "Hang Up By" in Flex Insights

This solution uses the [TaskRouter Workspace Callback Event URL](https://www.twilio.com/docs/taskrouter/api/event/reference#:~:text=TaskRouter%20will%20make,Event%20takes%20place.) and points it to a [Twilio Serverless Function](https://www.twilio.com/docs/serverless/functions-assets/functions). This Function listens for the `task.wrapup` event from TaskRouter, and if this is a "voice" Task, it will check to see who ended the Conference and update Flex Insights with either `customer` or `agent`.

For a more robust solution which logs `customer`, `agent`, or the unexpected `disconnect`, check out this other repo: https://github.com/bschinina-twilio/flex-insights-hang-up-by.

## Environment Variables
| Variable | Example Identifier |
| ----- | ---- |
| `WORKSPACE_SID` | WSxxxxxxxxxx

## Disclaimer
This software is to be considered "sample code", a Type B Deliverable, and is delivered "as-is" to the user. Twilio bears no responsibility to support the use or implementation of this software.
