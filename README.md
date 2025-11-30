AIRTABLE TO BREVO (n8n Workflow)
🚀 Overview

This project is an automated integration workflow between Airtable and Brevo (formerly Sendinblue), built using n8n.

The workflow retrieves records from Airtable, processes and formats the data, then syncs it automatically with the Brevo contacts list.
It is designed for businesses that need continuous, error-free data syncing between their internal database (Airtable) and their email marketing / CRM system (Brevo).

⚙️ Features
✅ 1. Scheduled Automations

A Schedule Trigger runs the workflow automatically at defined intervals (hourly, daily… depending on configuration).

✅ 2. Airtable Base Handling

Fetching all bases

Retrieving schema

Getting mapped fields to process the correct table and structure

✅ 3. Data Cleaning & Mapping

Custom JavaScript nodes process each record:

Formatting fields

Normalizing missing data

Mapping Airtable fields to Brevo fields

Removing unnecessary/duplicate values

✅ 4. Contact Sync with Brevo API

The workflow:

Sends data to Brevo using HTTP Request nodes

Uses loops to send multiple contacts

Automatically waits between requests to respect API rate limits

✅ 5. Conditional Logic

An IF node allows smart decision-making:

Only send contacts meeting certain conditions

Skip invalid or incomplete entries

✅ 6. Error Handling

Each request is wrapped with retry/wait logic to ensure high reliability.

🛠️ Workflow Structure (as seen in the editor)
Schedule Trigger
   → Get Many Bases
      → Get Base Schema
         → Edit Fields
            → HTTP Request (Airtable rows)
               → Code (Map data)
                  → Edit Fields 1
                     → IF
                        → Wait
                        ↓
                    Code (Process Loop Items)
                       → Loop over Items
                          → HTTP Request (Send to Brevo)
                              → Wait

🔒 Security

This workflow no longer contains any secrets.
All sensitive credentials (Airtable API Keys, Brevo API Keys) must be stored inside n8n credentials, never in plaintext files.

🧪 How to Use
1. Clone the repository
git clone https://github.com/{your_username}/from_Airtable_to_brevo-n8n-.git

2. Import the workflow into n8n

Open your n8n instance

Go to Workflows → Import

Upload the workflow JSON

3. Add required credentials

Airtable API Key

Brevo API Key

4. Update table IDs / list IDs to match your environment
5. Activate the workflow

Click Activate to run automatically.

📬 Output

Contacts are synced from Airtable to Brevo

Works fully automated

Handles large record sets with retries & safe looping

📄 License

This project is published under the MIT License.
