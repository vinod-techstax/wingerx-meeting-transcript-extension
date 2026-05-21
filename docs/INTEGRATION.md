# External Integration (Webhooks)

You can send transcripts to your external React application (or any backend) using the built-in Webhook feature.

## Setting Up the Webhook
1.  Open the **Meetings Page** (via the extension popup -> "Last 10 meetings").
2.  In the **"Set up webhooks"** section:
    - **Webhook URL:** Enter the endpoint of your React application or backend (e.g., `https://your-api.com/transcripts`).
    - **Auto-post:** Toggle this on if you want the extension to automatically send the transcript at the end of every meeting.
    - **Body Type:** Choose between **Simple** and **Advanced**.
3.  Click **Save**. Chrome will ask for permission to allow the extension to communicate with your URL.

## Payload Formats

### Simple Body
Best for quick logging or if you just need the full text as a string.
```json
{
  "webhookBodyType": "simple",
  "meetingSoftware": "Google Meet",
  "meetingTitle": "Project Sync",
  "meetingStartTimestamp": "05/19/2026, 12:00 PM",
  "meetingEndTimestamp": "05/19/2026, 1:00 PM",
  "transcript": "John Doe (12:05 PM)\nHello everyone...\n\nJane Smith (12:06 PM)\nHi John...",
  "chatMessages": "..."
}
```

### Advanced Body
Best for processing data in your React app, as it provides structured arrays.
```json
{
  "webhookBodyType": "advanced",
  "meetingSoftware": "Google Meet",
  "meetingTitle": "Project Sync",
  "meetingStartTimestamp": "2026-05-19T12:00:00.000Z",
  "meetingEndTimestamp": "2026-05-19T13:00:00.000Z",
  "transcript": [
    {
      "personName": "John Doe",
      "timestamp": "2026-05-19T12:05:00.000Z",
      "transcriptText": "Hello everyone"
    }
  ],
  "chatMessages": []
}
```

## Receiving Data in a React/Node.js App
Since webhooks are sent from the background script using a `POST` request with `application/json`, your endpoint should be configured to handle it.

### Example Express.js Endpoint:
```javascript
const express = require('express');
const app = express();
app.use(express.json());

app.post('/transcripts', (req, res) => {
  const data = req.body;
  console.log('Received transcript:', data.meetingTitle);
  // Process and save to your database
  res.status(200).send('Received');
});

app.listen(3000, () => console.log('Listening on port 3000'));
```

### Handling in React:
If you want to send data directly to a React app, you usually need a backend to receive the webhook first, which then pushes the data to the React app via WebSockets (e.g., Socket.io) or stores it in a database for the React app to fetch.

**Note:** The extension cannot send a webhook directly to a browser-only React app (localhost:3000) unless that React app is also running a server-side listener or you are using a tool like Ngrok to expose your local environment.
