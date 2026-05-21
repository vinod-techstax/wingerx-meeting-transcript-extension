# Wingerx Meeting Transcript
Simple Google Meet transcripts. Private and open source. 


# How to use Wingerx Meeting Transcript
![screenshot-2](/assets/screenshot-2.png)
Wingerx Meeting Transcript has two modes of operation.

**In both modes, transcript will be downloaded as a text file at the end of each meeting.**

- **Auto mode:** Automatically records transcripts for all meetings
- **Manual mode:** Switch on Wingerx Meeting Transcript by clicking on captions icon in Google Meet (CC icon)


<br />
<br />

# Integrating Wingerx Meeting Transcript with other tools using webhooks
You can integrate Wingerx Meeting Transcript with any tool that accepts data from a webhook. Refer the "Set up webhooks" page in the extension for details about the webhook body.
- Google Docs integration guide
- n8n integration guide

<br />
<br />

# FAQs

**1. Can I change the language of the transcript?**

Yes. Wingerx Meeting Transcript picks up the output of Google Meet captions. Google Meet captions supports variety of languages that you can choose from. Click the settings icon when captions start showing and change the language.

**2. I did not get any transcript at the end of the meeting.**

This could happen when:
1. New errors caused by Google Meet updates
2. Any unexpected events like network drop, browser crashes etc.

When this happens, it might be possible to recover the transcript, but recovery should be done before starting another meeting.
- Open the extension and click on "last 10 meetings". Click on "Recover last meeting" button present after the table.
- Wingerx Meeting Transcript will also attempt to auto-recover any missed transcripts, just before a new meeting starts.

<br />
<br />

# Privacy policy
Wingerx Meeting Transcript Chrome extension does not collect any information from users in any manner, except anonymous errors and transcript download timestamp. All processing/transcript storage happens within the user's Chrome browser and does not leave the device, unless you configure a webhook and choose to post data to your webhook URL.

<br />
<br />

# Notice
The transcript may not always be accurate and is only intended to aid in improving productivity. It is the responsibility of the user to ensure they comply with any applicable laws/rules.

<br />
<br />
