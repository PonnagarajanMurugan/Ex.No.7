# Exno.7-Develop a prompt-based application tailored to their personal needs, fostering creativity and practical problem-solving skills while leveraging the capabilities of large language models.

### Register no: 212222040115

## Aim: 
To develop a prompt-based application using ChatGPT - To demonstrate how to create a prompt-based application to organize daily tasks, showing the progression from simple to more advanced prompt designs and their corresponding outputs.

## AI Tools Required: 

1.ChatGPT (OpenAI API or interface)

2.Python (for CLI interface)

3.Optionally: JSON file for simple memory storage

## Explanation: 
### Prompt:
"Design a personal productivity assistant that can help manage daily tasks, schedule reminders, suggest wellness tips, and answer general queries. The assistant should interact using natural language and be adaptable to the user’s changing preferences over time."

This prompt guides the LLM to create intelligent and interactive responses that handle task management, scheduling, wellness advice, and more.

![download](https://github.com/user-attachments/assets/1f0956c6-772f-468d-b3fa-366818abde79)


## Procedure
### Core Requirements of the Assistant:

1.Add, view, and delete tasks via natural language

2.Set reminders

3.Provide daily wellness tips

4.Answer general queries (e.g., "What is AI?")

5.Adapt recommendations based on user feedback (simulate preference learning)

### Prompt Construction Examples:

1.Add Task:
"Remind me to submit my project report by 5 PM today."

2.View Tasks:
"What tasks do I have today?"

3.Wellness Tip Request:
"Give me a wellness tip."

4.Answer Query:
"What is machine learning?"

### Python Program:
```
import json
from datetime import datetime

# Simple memory simulation
try:
    with open('user_memory.json', 'r') as file:
        user_memory = json.load(file)
except FileNotFoundError:
    user_memory = {"tasks": [], "wellness_preferences": []}

def save_memory():
    with open('user_memory.json', 'w') as file:
        json.dump(user_memory, file, indent=4)

def add_task(task):
    user_memory['tasks'].append({"task": task, "timestamp": str(datetime.now())})
    save_memory()
    return "Task added successfully!"

def view_tasks():
    if not user_memory['tasks']:
        return "You have no tasks for today."
    return "\n".join([f"{i+1}. {t['task']}" for i, t in enumerate(user_memory['tasks'])])

def wellness_tip():
    tips = [
        "Drink at least 8 glasses of water today.",
        "Take short breaks every hour to stretch.",
        "Ensure you get at least 7 hours of sleep."
    ]
    # Optionally adapt tip based on user memory
    return tips[len(user_memory['wellness_preferences']) % len(tips)]

def main():
    print("=== Personal Productivity Assistant ===")
    while True:
        user_input = input("\nHow can I help you today? (type 'exit' to quit): ").lower()
        
        if "add task" in user_input or "remind me" in user_input:
            task = input("Please describe your task: ")
            print(add_task(task))
        elif "view tasks" in user_input or "what are my tasks" in user_input:
            print(view_tasks())
        elif "wellness tip" in user_input:
            tip = wellness_tip()
            print(f"Wellness Tip: {tip}")
            user_memory['wellness_preferences'].append(tip)
            save_memory()
        elif "exit" in user_input:
            print("Goodbye! Stay productive!")
            break
        else:
            print("I'm sorry, I can help you with adding tasks, viewing tasks, and providing wellness tips.")

if __name__ == "__main__":
    main()
```

### Collect Feedback and Adapt Responses:

The application stores wellness tips shown to the user in a file (user_memory.json) to simulate adaptation (preference memory).

The assistant shows different wellness tips based on previous interactions

### Sample Output:
```
=== Personal Productivity Assistant ===

How can I help you today? (type 'exit' to quit): remind me
Please describe your task: Submit the AI project report by 5 PM.
Task added successfully!

How can I help you today? (type 'exit' to quit): view tasks
1. Submit the AI project report by 5 PM.

How can I help you today? (type 'exit' to quit): wellness tip
Wellness Tip: Drink at least 8 glasses of water today.

How can I help you today? (type 'exit' to quit): wellness tip
Wellness Tip: Take short breaks every hour to stretch.

How can I help you today? (type 'exit' to quit): exit
Goodbye! Stay productive!
```

# Result: 
The lab exercise resulted in the creation of a prototype concept for a personal assistant powered by large language models. Students were able to:

1. Understand how to tailor LLM prompts to real-life applications.
   
2. Foster creativity by designing features suited to their personal or academic lives.
 
3. Learn prompt engineering techniques for optimal interaction with AI tools.
 
4. Experience the versatility and utility of generative AI in solving everyday problems.
