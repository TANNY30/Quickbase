
![quickbase](https://github.com/TANNY30/Quickbase/assets/129363580/6c14b70b-59ed-40a1-a765-c89fa274c611)


import requests
import json

# Replace with your values
QB_REALM_HOSTNAME = "your_quickbase_realm_hostname.quickbase.com"  # Replace with your QuickBase domain
USER_TOKEN = "your_user_token"  # Replace with your QuickBase user token

# Define table schema (replace with your field definitions)
table_schema = [
    {"f": {"label": "Field 1", "type": "TEXT"}},
    {"f": {"label": "Field 2", "type": "TEXT"}},
]

# ... (rest of the code as shown previously)

# Create records using the obtained table ID (assuming successful table creation)
if response.status_code == 200:
  table_id = response.json()["rid"]

  # Define record data (replace with your actual data structure)
  records = [
      {"f": {"fid": 2, "value": "Record 1 Value 1"}},
      {"f": {"fid": 3, "value": "Record 1 Value 2"}},
      # Add similar structures for records 2 to 4
      {"f": {"fid": 2, "value": "Record 5 Value 1"}},
      {"f": {"fid": 3, "value": "Record 5 Value 2"}},
  ]

  # Build the API URL for creating records
  url = f"https://{QB_REALM_HOSTNAME}/api/v1/records"

  # Set headers with authorization and content type
  headers = {
      "Authorization": f"QB-USER-TOKEN {USER_TOKEN}",
      "Content-Type": "application/json",
  }

  # Create data for the POST request
  data = {"records": records, "qid": table_id}

  # Send POST request to create records
  response = requests
