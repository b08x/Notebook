---
---

## aider


[Aider](https://aider.chat/) is a command line tool that lets you pair program with GPT-3.5/GPT-4, to edit code stored in your local git repository. You can start a new project or work with an existing repo. And you can fluidly switch back and forth between the aider chat where you ask GPT to edit the code and your own editor to make changes yourself. Aider makes sure edits from you and GPT are [committed to git](https://aider.chat/docs/faq.html#how-does-aider-use-git) with sensible commit messages. Aider is unique in that it [works well with pre-existing, larger codebases](https://aider.chat/docs/ctags.html).


## autogpt

https://github.com/Significant-Gravitas/AutoGPT/blob/master/QUICKSTART.md

https://georgesung.github.io/ai/autogpt-arch/


# llama.cpp
#LLM #llama 

```bash
./main -ngl 32 -m samantha-mistral-7b.Q4_K_M.gguf \
		--color -c 2048 --temp 0.7 --repeat_penalty 1.1 \
		-n -1 \
		-p "<|im_start|>system\n{system_message}<|im_end|>\n<|im_start|>user\n{prompt}<|im_end|>\n<|im_start|>assistant"
```


