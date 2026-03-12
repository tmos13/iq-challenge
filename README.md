# IQ Challenge

**A TMOS13 pack for cognitive profiling.**

Verbal reasoning. Numerical reasoning. Pattern recognition.
Spatial logic. Four sections, adaptive difficulty, scored profile.

Not a clinical IQ test — a rigorous cognitive challenge that produces
a meaningful profile of where your thinking is strongest.

---

### Four sections

- **Verbal Reasoning** — analogies, vocabulary in context, logical inference
- **Numerical Reasoning** — number series, arithmetic reasoning, data interpretation
- **Pattern Recognition** — sequence completion, matrix reasoning, odd-one-out
- **Spatial Reasoning** — mental rotation, folding, 2D/3D transformation

### The deliverable

`cognitive_profile` — section scores, overall band, strongest and weakest
domains, cognitive signature.

---

### Pack structure

```
iq-challenge/
├── README.md
├── header.yaml
└── MANIFEST.md
```

---

### Run it yourself

This is a reference implementation of a TMOS13 pack. Clone the repo,
load the protocol into any Claude API session, and run it directly.

**Minimum setup:**

```python
import anthropic

with open("MANIFEST.md", "r") as f:
    manifest = f.read()

client = anthropic.Anthropic()

messages = []

print("Session started. Type your message.\n")

while True:
    user_input = input("You: ")
    messages.append({"role": "user", "content": user_input})

    response = client.messages.create(
        model="claude-opus-4-5-20251101",
        max_tokens=1024,
        system=manifest,
        messages=messages
    )

    reply = response.content[0].text
    messages.append({"role": "assistant", "content": reply})
    print(f"\nAssistant: {reply}\n")
```

Requires: `pip install anthropic` and an `ANTHROPIC_API_KEY` environment variable.

For the full TMOS13 engine — pack state management, vault, deliverables,
multi-cartridge routing — visit [tmos13.ai](https://tmos13.ai).

---

**TMOS13, LLC** · Deploy Yourself™
