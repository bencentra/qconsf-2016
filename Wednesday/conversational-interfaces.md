# [Design Guidelines for Conversational Interfaces](https://qconsf.com/sf2016/presentation/design-guidelines-voice-interfaces)

Wednesday, Nov. 9 2016

Angie Terrell

Conversations, talking with computers as if they were human. Prevalent in pop culture since _War Games_

Will we ever be able to talk to a machine as if it were human?

Where we are today: Devices like the Amazon Echo ("Alexa"), don't understand what or why its saying, can only regurgitate.

UI Design for Voice:
* Select the tasks to support

Principles:
1) Prompt and Response
2) Recognition over Recall
3) Speech Requires Focus
4) Always Provide a Fallback
5) Respect People's Time

Prompt and Response
* Don't pretend to be human (hyperbole)
* Intents: what is the user giving the system (in terms of info)
  * No Intent: "Hi Weatherbot" > Prompt for local weather or weather in city
  * Partial Intent: "Hi Weatherbot, what is the weather in Madison?" > Prompt to specify which Madison (state)
  * Full Intent: "What is the weather in San Francisco, CA?" > Give the answer
* Close-ended: humans understand context, chatbots don't!
  * Yes/No questions, clear actions, don't leave anything hanging
* Options: Provide clear options, distinct from question, avoid tricky answers:
  * "Would you like french fries or salad?" vs "Which side would you like: french fries or salad"
  * Providing buttons for on-screen interfaces, keep it async

Recognition over Recall
* "When there's no GUI in a product to guide us, our memory becomes the UI"
* Catch-all: "help" options!
* Build the system to support/learn nuances of commands ("price", "cost", "how much", etc)

Speech Requires Focus
* Words as audio != text on screen
* "People lose attention after 10-15 seconds of listening to a prompt"
* Visual interfaces are more permanent, can be read at a different pace/time
* Siri - Voice + GUI, don't need to issue a second voice command to complete an action

Always Provide a Fallback
* Reply to incorrect prompts with expected options
* Hybrid Example: lola, a travel chatbot, hybrid machine and customer service rep.

Respect People's Time
* Keep prompts as short as possible while providing all the info as clearly as possible
* Allow the user to drop out of a command, know how to handle unsaved data over time (a day? an hour?)

Recap:
* At the present, we cannot interact with machines like humans
* Designing a conversational UI does not free us from the most substantial problems of user interface design
* Employ the five guidelines for conversational UI
