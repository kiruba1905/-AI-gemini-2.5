# -AI-gemini-2.5
import os
from google import genai
from dotenv import load_dotenv

load_dotenv()

# Gemini API key from env var
api_key = os.getenv("GEMINI_API_KEY")
if not api_key:
    raise SystemExit("Error: set GEMINI_API_KEY environment variable")

client = genai.Client()

def ask_ai(question):
    response = client.models.generate_content(model="gemini-2.5-flash", contents=question)
    return response.text

print("AI Chat Bot (powered by Gemini). Type 'quit' to exit.")
while True:
    user_input = input("You: ")
    if user_input.lower() == 'quit':
        break
    response = ask_ai(user_input)
    print("AI:", response)
