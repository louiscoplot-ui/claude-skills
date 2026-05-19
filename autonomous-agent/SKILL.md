---
name: autonomous-agent
description: >
  Design and build autonomous AI agents, self-improving bots, multi-agent systems, agentic loops.
  Use when user says "build an autonomous agent", "self-improving bot", "agent that runs itself",
  "multi-agent system", "agentic workflow", "AI that improves over time", "autonomous pipeline",
  "agent that makes decisions", "build a bot that thinks".
---
# Autonomous Agent

## ReAct Loop
while not done:
    thought = llm.think(context, tools_available)
    action = llm.choose_action(thought)
    result = execute_action(action)
    context.update(result)
    done = llm.check_completion(context)

## Self-Improving Pattern
class SelfImprovingAgent:
    def run(self, task):
        past = self.memory.search(task)        # retrieve similar tasks
        result = self.execute(task, context=past)
        score = self.evaluate(result)          # score output quality
        self.memory.store(task, result, score) # learn for next time
        if self.is_degrading():
            self.recalibrate()
        return result

## Multi-Agent Orchestrator
agents = { scraper, analyzer, writer, validator }
data -> scraper -> analyzer -> writer -> validator -> output

## Memory Systems
- Short-term: deque(maxlen=20) for context window
- Long-term: ChromaDB vector similarity search
- Episodic: SQLite log of task/action/result/score

## Tool Use
tools = { search_web, read_file, write_file, run_code, call_api }
Agent picks tool -> executes -> feeds result back -> continues loop

## Stack
LLM: Claude API / OpenAI / Ollama
Vector DB: ChromaDB (local) / Pinecone (cloud)
Queue: Celery + Redis
Orchestration: LangGraph / custom ReAct
