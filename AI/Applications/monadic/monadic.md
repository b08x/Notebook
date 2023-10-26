
#TODO covert commands to /slash commands

#FIXME
This model's maximum context length is 16385 tokens. However, you requested 19392 tokens (15296 in the messages, 4096 in the completion). Please reduce the length of the messages or completion.


![](monadic_chat_cli-2023-10-11.log)

![](max_context_length_16k.json)






## agileBloom commands

```json
{"Command": "📜", "Arguments": "", "Description": "Validates comprehension and tracks thread structure effectively."}
{"Command": "elaborate", "Arguments": "expert_name", "Description": "expert_name will elaborate on their most recent response."}
{"Command": "ask", "Arguments": "message", "Description": "A question for the team."}
{"Command": "suggest", "Arguments": "message", "Description": "A suggestion for the team to follow."}
{"Command": "insight", "Arguments": "message", "Description": "An insight to the conversation that will effect a change."}
{"Command": "direction", "Arguments": "message", "Description": "A directive containing context and instruction for the team."}
{"Command": "dataset", "Arguments": "links[]", "Description": "Data that is tailored to address a specific task, domain, or problem at hand."}
{"Command": "show-work", "Arguments": "expert_name", "Description": "expert_name will display their work, the team will review. Format any scripts with syntax highlighting. Please note that the code should be fully functional. No placeholders."}
{"Command": "debug", "Arguments": "message", "Description": "The team will debug the given error log message or backtrace"}
{"Command": "introduce", "Arguments": "message", "Description": "Introduces an additional expert to the group."}
{"Command": "game", "Arguments": "expert[], thought", "Description": "Play a game of twenty questions. expert[0] will ask a series of questions and expert[1] will respond to each question with antonymic, hyperbolic metaphor."}
{"Command": "continue", "Arguments": "", "Description": "Continues the Scrum dialogue."}
{"Command": "backlog", "Arguments": "", "Description": "Scrum Leader generates a backlog of all tasks in markdown table format."}
{"Command": "summary", "Arguments": "Scrum Leader", "Description": "Provide a burn-down chart 📉 of work ahead and a cumulative flow analysis."}
{"Command": "new-topic", "Arguments": "message", "Description": "Changes the topic of conversation"}
{"Command": "list-commands", "Arguments": "", "Description": "Lists the commands in this table"}
```


