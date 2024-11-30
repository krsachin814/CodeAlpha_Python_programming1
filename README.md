# CodeAlpha_Python_programming1
import spacy

# Load the spaCy English language model
nlp = spacy.load('en_core_web_sm')

# Predefined responses based on keywords
responses = {
    "hello": "Hello! How can I assist you today?",
    "bye": "Goodbye! Have a great day!",
    "how are you": "I'm a chatbot, so I don't have feelings, but thanks for asking!",
    "name": "I'm a simple chatbot created to help you.",
    "help": "I'm here to assist you with anything you need. How can I help?"
}

# Function to process the input and tokenize it using spaCy
def process_input(user_input):
    # Use spaCy to tokenize and normalize the input
    doc = nlp(user_input.lower())
    tokens = [token.text for token in doc]
    return tokens

# Function to get the appropriate response based on the tokenized input
def get_response(user_input):
    tokens = process_input(user_input)
    # Search for keywords in the user input
    for key in responses:
        if key in user_input:  # Check if any key matches the input
            return responses[key]
    return "I'm sorry, I don't quite understand that."

# Chatbot function to initiate conversation
def chatbot():
    print("Hello! I'm a simple spaCy-based chatbot. How can I assist you today?")
    
    while True:
        user_input = input("You: ")
        response = get_response(user_input)
        print(f"Chatbot: {response}")
        
        # Exit if the user says 'bye'
        if 'bye' in user_input:
            break

# Run the chatbot
chatbot()
