# tr-hang-up-by-insights
Back-end solution to add "hang_up_by" data to Flex Insights with a Twilio Serverless Function and the TaskRouter Workspace Callback Event URL.

This solution only populates the following data inside of "Hang Up By":
- `customer`
- `agent`

For a more robust solution, check out this other repo: https://github.com/bschinina-twilio/flex-insights-hang-up-by

## Environment Variables
| Variable | Example Identifier |
| ----- | ---- |
| `WORKSPACE_SID` | WSxxxxxxxxxx

## Disclaimer
This software is to be considered "sample code", a Type B Deliverable, and is delivered "as-is" to the user. Twilio bears no responsibility to support the use or implementation of this software.
