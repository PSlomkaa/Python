import random
import re

# Define responses for the chatbot
responses = {
    "hello": ["Hello!", "Hi there!", "Hey!"],
    "hi": ["Hello!", "Hi there!", "Hey!"],
    "how are you": ["I'm just a computer program, but I'm doing well. How about you?", "I don't have feelings, but thanks for asking!"],
    "goodbye": ["Goodbye!", "See you later!", "Bye now!"],
    "tell me a joke": ["Why don't scientists trust atoms? Because they make up everything!", "I'm not a stand-up comedian, but here's a joke: Knock, knock. Who's there? Boo. Boo who? Don't cry, it's just a joke!"],
    "what's your favorite color": ["I'm not sure I have a favorite color. What's yours?", "I don't have the ability to see colors, but I'm curious, what's your favorite color?"],
    "who created you": ["you"],
    "i'm stuck" : ["Don't worry, sepbro is going to help you"]
    "help": ["I'm here to chat and answer questions. Feel free to ask me anything!", "If you're not sure what to ask, you can say 'help' for suggestions."],
    "what is the meaning of life": ["The meaning of life is a deep philosophical question. Some say it's 42, but I'm not so sure!", "The meaning of life is a question that has puzzled humanity for centuries. What do you think it is?"],
    "tell me a fun fact": ["Sure, here's a fun fact: Honey never spoils. Archaeologists have even found pots of honey in ancient Egyptian tombs that are over 3,000 years old and still perfectly edible!", "Here's a fun fact: Octopuses have three hearts!"],
    "favorite book": ["I don't read books, but I've heard '1984' by George Orwell and 'To Kill a Mockingbird' by Harper Lee are popular choices. What's your favorite book?", "I don't have personal preferences for books, but I'm always interested in hearing about people's favorites. What's your favorite book?"],
    "music recommendation": ["I can recommend music based on your mood or preferences. What kind of music are you in the mood for?", "Sure, I can recommend music! What genre or artist are you interested in?"],
    "weather": ["I'm sorry, I don't have access to real-time weather information.", "You might want to check a weather website or app for the latest updates."],
    "news": ["I don't have access to real-time news updates, but you can check a trusted news website or app for the latest news.", "Staying informed is important. You can get the latest news from a reliable news source."],
    "movie recommendation": ["I can recommend a movie based on your preferences. What genre are you interested in?", "Sure, I can suggest a movie! What type of movie are you in the mood for?"],
    "default": ["I'm not sure I understand.", "Could you please rephrase that?", "I'm just a simple chatbot."],
}

# Function to generate a response to user input
def generate_response(user_input):
    user_input = user_input.lower()
    
    # Check for specific keywords using regular expressions
    if re.search(r'\b(weather|temperature)\b', user_input):
        return random.choice(responses["weather"])
    
    if re.search(r'\b(news|headlines)\b', user_input):
        return random.choice(responses["news"])
    
    if re.search(r'\b(movie|film)\b', user_input):
        return random.choice(responses["movie recommendation"])
    
    for key, value in responses.items():
        if key in user_input:
            return random.choice(value)
    
    return random.choice(responses["default"])

# Main loop
print("Chatbot: Hello! How can I help you today?")
while True:
    user_input = input("You: ")
    if user_input.lower() == "bye":
        print("Chatbot: Goodbye!")
        break
    response = generate_response(user_input)
    print("Chatbot:", response)
