# n8n-Audio-Transcription
Provides transcription capabilities through n8n and AssemblyAI when starting with a WordPress post or audio link.

---

# AssemblyAI Audio to Text Transcription

The AssemblyAI Audio to Text Transcription n8n workflow uses AssemblyAI to transcribe an audio file when given the audio link. There is functionality to split the transcript into paragraphs so that it is easier for the user to read. This is one part of a larger workflow that me and my colleagues are designing, but it is possible to make it function by itself.

---

## How It Works

This workflow can take inputs of either a WordPress Post or an audio link, both of which eventually ouput as a Google Doc, with the WP Post being updated if the input was a WP Post. To switch the input, deactivate the other form node and activate the desired node.

When executing the workflow, a popup will appear.
- If the WordPress post form was activated, enter the **post ID** into the text box.
- If the audio link form was activated, enter the audio link into the text box.

If the input was a WP post, OpenAI will extract the information out of it, including the audio link within. Then, both inputs share the same path; turn the audio link into a file, uploading the file to AssemblyAI, transcribing the file, and outputting the transcription.

Next, a Google Doc will be created and populated with the transcript, and then will be sent off for approval. You may edit the transcript and then click approve, which will send the updated transcript to OpenAI to summarize it. The summary will then be added to the document and sent for a final approval.

Finally, the workflow will output the completed Google Doc, updating the WordPress post if there was one to begin with.

---

## Workflow Set Up

- Enter your WordPress credentials on all WP nodes
- Enter your Google Docs credentials on all Google Docs nodes
- Enter your Gmail credentials on all Gmail nodes
- Enter your AssemblyAI credentials on all AssemblyAI nodes
- Enter your OpenAI credentials on all OpenAI nodes
- Enter your WordPress domain when prompted (if you plan to start with a WordPress post)
- Enter the email address used for approvals

---

## Current Bugs

- The output of the workflow is the transcript in a Google Doc. I have not found a way to be able to change the document permissions using n8n. This will present problems when trying to give the document to a different user or a sub-workflow using automation.
- This problem is also present when giving emails for approvals. The Google Doc will be emailed to the email address provided. If the same Google account is used for each, it will be fine, however, if a different account is to approve the transcript, access to the document will not be given to that account.

---

## Bug Workarounds

- A workaround to the permission bug is that the same Google account is used for the creation of the document and the transcript approvals, and, when viewing the document, the user manually sets the Google Doc permissions.
