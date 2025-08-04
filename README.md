# Ibminternship
# Description
The Travel Planner Agent is an AI-powered chatbot designed to assist users in planning trips quickly, smartly, and personally. Integrated with IBM Cloud Lite and IBM Granite AI models, the chatbot interacts with users to understand their travel preferences — such as destination, dates, budget, and interests — and then generates personalized travel plans.

It suggests ideal destinations, creates detailed itineraries, recommends transport and accommodation options, and integrates live data such as weather updates and maps. The assistant can manage bookings, notify users of schedule changes, and provide real-time travel support, transforming complex travel planning into a smooth, enjoyable experience.

💡 Key Features:
Conversational trip planning via chatbot

Smart destination suggestions based on preferences

Itinerary generation and optimization

Transport & hotel recommendations

Live weather and location info

Real-time alerts and support

Powered by IBM Watson Assistant, IBM Granite & Cloud Functions
# code
import requests

# NOTE: you must manually set API_KEY below using information retrieved from your IBM Cloud account (https://eu-gb.dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/ml-authentication.html?context=wx)
API_KEY = "<your API key>"
token_response = requests.post('https://iam.cloud.ibm.com/identity/token', data={"apikey": API_KEY, "grant_type": 'urn:ibm:params:oauth:grant-type:apikey'})
mltoken = token_response.json()["access_token"]

header = {'Content-Type': 'application/json', 'Authorization': 'Bearer ' + mltoken}

# NOTE:  manually define and pass the array(s) of values to be scored in the next line
payload_scoring = {"messages":[{"content":"","role":""}]}

response_scoring = requests.post('https://eu-gb.ml.cloud.ibm.com/ml/v4/deployments/1de24b98-a8f9-4b3c-aea0-f4047a8432fe/ai_service_stream?version=2021-05-01', json=payload_scoring,
 headers={'Authorization': 'Bearer ' + mltoken})

print("Scoring response")
try:
    print(response_scoring.json())
except ValueError:
    print(response_scoring.text)
except Exception as e:
    print(f"An unexpected error occurred: {e}")
# output photos
<img width="1920" height="1080" alt="Screenshot (579)" src="https://github.com/user-attachments/assets/7cf1f519-eabf-4d3e-84df-7f3b76f0fe4c" />
<img width="1920" height="1080" alt="Screenshot (580)" src="https://github.com/user-attachments/assets/8adacccf-38dd-419b-a83a-dda1beacc626" />
<img width="1920" height="1080" alt="Screenshot (583)" src="https://github.com/user-attachments/assets/04a19335-8807-4309-a217-11b5cb6d37be" />


