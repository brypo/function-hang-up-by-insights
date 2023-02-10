
exports.handler = async function (context, event, callback) {
    const client = context.getTwilioClient()
    const workspaceSid = context.WORKSPACE_SID
    const response = new Twilio.Response()

    const { TaskSid, TaskAttributes, EventType, TaskChannelUniqueName } = event

    if (EventType == "task.wrapup" && TaskChannelUniqueName === "voice") {
        const taskAttributes = JSON.parse(TaskAttributes)
        const { conference } = taskAttributes

        try {
            let endingCallSid = await getConferenceEndingCall(client, conference.sid)
            console.log(`ending call sid: ${endingCallSid}`)

            if (endingCallSid === conference.participants.customer) {
                console.log(`ending call sid is customer`)
                await updateTaskAttributes(client, workspaceSid, TaskSid, taskAttributes, "customer")
            }
            else {
                console.log(`ending call sid is agent`)
                await updateTaskAttributes(client, workspaceSid, TaskSid, taskAttributes, "agent")
            }
            return callback(null, response)
        }
        catch (e) {
            console.error(e)
            response.setStatusCode(500)
            return callback(null, response)
        }
    }

    return callback(null, response)
}


const getConferenceEndingCall = async (client, confSid) => {
    let conf = await client.conferences(confSid).fetch()
    
    return conf.callSidEndingConference
}


const updateTaskAttributes = async (client, workspaceSid, taskSid, attributes, hangUpBy) => {
    let updatedAttributes

    if (attributes.hasOwnProperty("conversations")) {
        updatedAttributes = { ...attributes }
        updatedAttributes.conversations.hang_up_by = hangUpBy
    }
    else {
        updatedAttributes = { ...attributes, conversations: { hang_up_by: hangUpBy } }
    }

    await client.taskrouter.v1.workspaces(workspaceSid)
        .tasks(taskSid)
        .update({
            attributes: JSON.stringify(updatedAttributes)
        })
}
