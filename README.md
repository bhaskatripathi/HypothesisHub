# HypothesisHub
HypothesisHub is an AI Tool for Automated Research Question and Hypothesis Generation from a given Scientific Literature. It applies a chain of thought process to generate research questions and hypotheses from given scientific literature. The tool uses OpenAI and Langchain to generate questions and hypotheses from the given text.

## Features
- Generates research questions from a given scientific literature
- Generates a null hypothesis (H0) and an alternate hypothesis (H1) for each research question
- Handles cases where either H0 or H1 is not present
- Automatically generates missing H1 using the LLMChain if needed
- Negates hypothesis statement if H0 is missing

## Sequence Diagram
``` mermaid
sequenceDiagram
    participant User
    participant OpenAI
    participant ResearchAndHypothesisGenerator

    User->>+ResearchAndHypothesisGenerator: provide scientific literature
    ResearchAndHypothesisGenerator->>+research_question_template: instantiate prompt template
    research_question_template->>+ResearchAndHypothesisGenerator: return prompt template
    ResearchAndHypothesisGenerator->>+research_question_chain: instantiate LLMChain
    research_question_chain->>+ResearchAndHypothesisGenerator: return LLMChain
    ResearchAndHypothesisGenerator->>+OpenAI: generate research questions
    OpenAI->>+research_question_chain: generate research questions
    research_question_chain->>+OpenAI: return research questions
    OpenAI->>-ResearchAndHypothesisGenerator: return research questions
    ResearchAndHypothesisGenerator->>+hypothesis_prompt_template: instantiate prompt template
    hypothesis_prompt_template->>+ResearchAndHypothesisGenerator: return prompt template
    ResearchAndHypothesisGenerator->>+hypothesis_chain: instantiate LLMChain
    hypothesis_chain->>+ResearchAndHypothesisGenerator: return LLMChain
    ResearchAndHypothesisGenerator->>+OpenAI: generate hypotheses
    OpenAI->>+hypothesis_chain: generate hypotheses
    hypothesis_chain->>+OpenAI: return hypotheses
    OpenAI->>-ResearchAndHypothesisGenerator: return hypotheses
    ResearchAndHypothesisGenerator->>-User: return research questions and hypotheses
```
## Output
![Output image](https://github.com/bhaskatripathi/HypothesisHub/blob/main/output.png)
