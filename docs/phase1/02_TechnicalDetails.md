## Project Setup

* Create a Project Strucutre

'''bash
mkdir resume-screener-ai
uv init --package .
uv sync
'''

* Installing dependencies
'''bash
uv add langgraph python-dotenv
'''

* Models:

    * We will start with gemini models
    * We will use open ai gpt
    * We will use Bedrock from AWS
    * We will use Azure AI Foundry/Azure Open AI
    * We will be using local models hosted on ollama



### PART 1 - Defining the state

* InterviewRound

```python

class InterviewRound(TypedDict):
    round_number: int
    slot: str
    feedback: str|None
    decision: Literal["next_round","rejct","offer"]

class CandidateInterview(TypedDict):
    candidate_id: str
    status: str
    currnet_round: int
    history: List[InterviewRound]
    
class State(TypedDict):
    job_id: str
    job_description: str
    resumes: list[str]
    screening_result: list[dict]
    interviews: List[CandidateInterview]
    hr_report: str

```