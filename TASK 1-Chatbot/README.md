import random
import datetime
import json

class SmartConversationEngine:
    def __init__(self):
        self.context = {}
        self.conversation_memory = {}
        self.emotion_states = ['curious', 'helpful', 'enthusiastic', 'analytical']
    
    def generate_contextual_response(self, user_input):
        # Unique approach with multiple response generation strategies
        user_input = user_input.lower().strip()
        
        # Contextual and dynamic response generation
        response_strategies = {
            'greeting': [
                f"Hello! My current mood is {random.choice(self.emotion_states)}.",
                f"Greetings! It's {datetime.datetime.now().strftime('%I:%M %p')}.",
                "Welcome! How can I assist you today?"
            ],
            'time': [
                f"The current time is {datetime.datetime.now().strftime('%I:%M %p')}.",
                f"Right now, my internal clock shows {datetime.datetime.now().strftime('%H:%M')}."
            ],
            'help': [
                "I'm here to help! What specific information do you need?",
                "Your query intrigues me. Could you provide more details?",
                "I'm ready to assist you with my full computational capacity!"
            ]
        }
        
        # Intelligent pattern matching
        if any(word in user_input for word in ['hi', 'hello', 'hey']):
            return random.choice(response_strategies['greeting'])
        
        elif 'time' in user_input:
            return random.choice(response_strategies['time'])
        
        elif 'help' in user_input or 'assist' in user_input:
            return random.choice(response_strategies['help'])
        
        # Fallback mechanism
        return "I'm processing your input. Could you rephrase or be more specific?"
    
    def learn_from_interaction(self, user_input, response):
        # Unique learning mechanism
        current_hour = datetime.datetime.now().hour
        self.conversation_memory[current_hour] = {
            'input': user_input,
            'response': response,
            'timestamp': datetime.datetime.now()
        }

def interactive_chat():
    bot = SmartConversationEngine()
    print("Intelligent Conversation Agent: Ready to chat! Type 'bye' to exit.")
    
    while True:
        user_input = input("You: ")
        
        if user_input.lower() in ['bye', 'exit', 'quit']:
            print("Agent: Goodbye! Hope I was helpful.")
            break
        
        response = bot.generate_contextual_response(user_input)
        bot.learn_from_interaction(user_input, response)
        print("Agent:", response)

if __name__ == "__main__":
    interactive_chat()
