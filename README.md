# n8n-Audio-Transcription-And-Summary-Creation
Provides transcription capabilities and summary creation through n8n and AssemblyAI when starting with a WordPress post or audio link. Approvals will be sent via gmail and the output will be a google doc.

<img width="2000" height="257" alt="image" src="https://github.com/user-attachments/assets/c91a17c7-d26a-49cc-a105-14de0aeffa06" />
- What the workflow should look like

---

# 🔉➡️📄 AssemblyAI Audio to Text Transcription

The AssemblyAI Audio to Text Transcription n8n workflow uses AssemblyAI to transcribe an audio file when given the audio link. There is functionality to split the transcript into paragraphs so that it is easier for the user to read. This is one part of a larger workflow that me and my colleagues are designing, but it is possible to make it function by itself.

---

## 📃 How It Works

This workflow can take inputs of either a WordPress Post or an audio link, both of which eventually ouput as a Google Doc, with the WP Post being updated if the input was a WP Post. To switch the input, deactivate the other form node and activate the desired node.

<img width="1816" height="831" alt="image" src="https://github.com/user-attachments/assets/29d9c647-c0d3-46e9-837a-a73d67028517" />
- WordPress post is the input since the audio link form is deactivated

--

<img width="1821" height="838" alt="image" src="https://github.com/user-attachments/assets/ddb96dae-984d-4941-ad22-2855961db025" />
- Audio link is the input since the WordPress post form is deactivated

--

When executing the workflow, a popup will appear.
- If the WordPress post form was activated, enter the **post ID** into the text box.
- If the audio link form was activated, enter the audio link into the text box.

<img width="1216" height="1303" alt="image" src="https://github.com/user-attachments/assets/c7a20a1f-b8bb-4813-a4ab-5eeaa526e07d" />
- Example of a popup that appears when the WP post form is activated.

--

If the input was a WP post, OpenAI will extract the information out of it, including the audio link within. Then, both inputs share the same path; turn the audio link into a file, uploading the file to AssemblyAI, transcribing the file, and outputting the transcription.

<img width="1095" height="260" alt="image" src="https://github.com/user-attachments/assets/3a57e84b-4df0-40da-8c9a-3932b46af1be" />

--

Next, a Google Doc will be created and populated with the transcript, and then will be sent off for approval. You may edit the transcript and then click approve, which will send the updated transcript to OpenAI to summarize it. The summary will then be added to the document and sent for a final approval.

<img width="1352" height="399" alt="image" src="https://github.com/user-attachments/assets/3f041582-84c3-4743-b02c-96ca132a2000" />

<img width="1657" height="782" alt="image" src="https://github.com/user-attachments/assets/26dd13b1-a9ad-4b93-92e2-adbe116e330d" />
- This is what an approval email would look like

--

Finally, the workflow will output the completed Google Doc, updating the WordPress post if there was one to begin with.

<img width="768" height="325" alt="image" src="https://github.com/user-attachments/assets/910665f9-d5b6-4ff3-86a4-70fcf2722a4f" />

---

## 🔨 Workflow Set Up

- Enter your WordPress credentials on all WP nodes
- Enter your Google Docs credentials on all Google Docs nodes
- Enter your Gmail credentials on all Gmail nodes
- Enter your AssemblyAI credentials on all AssemblyAI nodes
- Enter your OpenAI credentials on all OpenAI nodes
- Enter your WordPress domain when prompted (if you plan to start with a WordPress post)
- Enter the email address used for approvals

---

## 📝 Important Notes

If the file size is too large, the workflow may error, disconnect from the server, timeout, or be infinitely "working" while doing nothing. I think this is due to memory limitations in n8n, and there is nothing that can be done about it except upgrading to a better n8n plan. Sometimes this happens, but sometimes it does not, it could depend on others using the n8n server at the same time. I don't have a great solution to this except to tell you to upload smaller files if this happens.
