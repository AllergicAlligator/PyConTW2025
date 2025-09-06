---
icon: material/lightbulb-auto-outline
---

# :material-lightbulb-auto-outline: AutoDocs

We will show how to:

:material-numeric-1-circle: use python to modify mkdocs.yml.   
:material-numeric-2-circle: get response from LLM.  
:material-numeric-3-circle: put :material-numeric-1-circle: and :material-numeric-2-circle: together. 

## 1️⃣ Modifying mkdocs.yml

``` python
import yaml

class MyDumper(yaml.Dumper):
    def increase_indent(self, flow=False, indentless=False):
        return super(MyDumper, self).increase_indent(flow, False)

# Create a list of filenames
new_pages = []
for i in range(5):
    new_pages.append(f"lesson{i}.md")

# We have ["lesson0.md", "lesson1.md", "lesson2.md", "lesson3.md", "lesson4.md"] in new_pages now

# Read mkdocs.yml
with open("mkdocs.yml", "r", encoding="utf-8") as f:
    config = yaml.safe_load(f)

print(config)

# Add filename list to nav
config["nav"] = new_pages

# Write mkdocs.yml
with open("mkdocs.yml", "w", encoding="utf-8") as f:
    yaml.dump(config, f, sort_keys=False, allow_unicode=True, Dumper=MyDumper)
```

## 2️⃣ ollama

* [https://ollama.com/](https://ollama.com/)
* [Open LLM Models](https://ollama.com/search)
* [https://github.com/ollama/ollama-python](https://github.com/ollama/ollama-python)

```mermaid
flowchart LR
    A[Python Code] <--> B[Ollama Python Library]
    B <--> C[Ollama]
    C <--> D[LLM]
```

:material-numeric-1-circle: Ollama Server

To download a model, run the following command:

```bash
ollama pull llama3.2
```

:material-numeric-2-circle: Ollama Python Library

```bash
pip install ollama
```

```python title="Regular Usage"
from ollama import chat
from ollama import ChatResponse

response: ChatResponse = chat(model='gemma3', messages=[
  {
    'role': 'user',
    'content': 'Why is the sky blue?',
  },
])
print(response['message']['content'])
# or access fields directly from the response object
print(response.message.content)
```

```python title="Streaming Response" hl_lines="6 9-10"
from ollama import chat

stream = chat(
    model='gemma3',
    messages=[{'role': 'user', 'content': 'Why is the sky blue?'}],
    stream=True,
)

for chunk in stream:
  print(chunk['message']['content'], end='', flush=True)
```

## 3️⃣ Autodocs using LLM

```python
import os
import re
import yaml
import ollama

class MyDumper(yaml.Dumper):
    def increase_indent(self, flow=False, indentless=False):
        return super(MyDumper, self).increase_indent(flow, False)

# 
MAIN_TOPIC = "Python Tutorial"
TOPIC_NUMBER = 5
MODEL_NAME = "llama3.2"

prompt = f"""Please design {TOPIC_NUMBER} subtopics for the main topic "{MAIN_TOPIC}".  
For each subtopic, write a complete tutorial in Markdown format (including title and sections).  
At the beginning of each subtopic, add <<<START>>> and at the end add <<<END>>>.  

Do not include any HTML tags inside the Markdown.  
Ensure that code blocks are separated from other content by one blank line.  

Here are 3 example subtopics for reference:  

<<<START>>>
# Subtopic 1

Content 1
<<<END>>>

<<<START>>>
# Subtopic 2

Content 2
<<<END>>>

<<<START>>>
# Subtopic 3

Content 3
<<<END>>>

And so on...  

Please make sure that <<<START>>> and <<<END>>> always come in pairs.  
"""

response = ollama.chat(
    model=MODEL_NAME,
    messages=[
        {"role": "user", "content": prompt}
    ]
)

output_text = response["message"]["content"]

with open("output.txt", "w", encoding="utf-8") as f:
    f.write(output_text)


# Check if docs exists
os.makedirs("docs", exist_ok=True)

# Extract content between START and END using re
# Find all START...END blocks
matches = re.findall(r'<<<START>>>(.*?)<<<END>>>', output_text, re.DOTALL)

new_pages = []

# Save files one by one
for i, content in enumerate(matches, start=1):
    filename = f"lesson{i}.md"
    new_pages.append(filename)
    with open(f"docs/{filename}", "w", encoding="utf-8") as f:
        f.write(content.strip())  # remove blanks
    print(f"{filename} saved!")

# Update mkdocs.yml
with open("mkdocs.yml", "r", encoding="utf-8") as f:
    config = yaml.safe_load(f)

config["nav"] = new_pages

with open("mkdocs.yml", "w", encoding="utf-8") as f:
    yaml.dump(config, f, sort_keys=False, allow_unicode=True, Dumper=MyDumper)

print("mkdocs.yml updated!")
```
