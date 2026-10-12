# Conversational Multi-Agent Music Recommender

A personal project built in high school, exploring how specialized LLM agents can turn a conversation into mood-aware music recommendations. This repository preserves the original notebook design, with English prompts and API keys loaded from environment variables.

## Core idea

Music discovery starts with understanding the listener. A conversational agent uses Socratic-style questions to uncover mood and musical preferences. A profile builder and a separate critic then refine that context before a recommender selects tracks and retrieves Last.fm links.

```text
Conversation → Profile Builder ↔ Profile Critic → Recommendations → Link Retrieval
```

## What makes the design forward-looking

- **Specialized agents:** Conversation, profiling, review, recommendation, and tool execution have distinct responsibilities.
- **A critique-and-refine loop:** A separate agent checks the profile before it informs recommendations, while accounting for how much information the user supplied.
- **Contextual personalization:** Recommendations consider both musical taste and the listener's current emotional state, using conversation rather than requiring a listening-history dataset.
- **Adaptive orchestration:** An LLM-based router directs requests and feedback, including profile revisions and unavailable links, to the appropriate agent.
- **Tool-backed discovery:** A name-normalization agent handles Chinese and English track metadata; a registered function searches Last.fm for track-page links.

The distinctive idea is the combination of conversational context, agent collaboration, and external tools in one recommendation workflow. This is an exploratory prototype, with no benchmarked claim of recommendation quality.

## Run

Requires Python, Jupyter, AutoGen/AG2, the OpenAI client, `requests`, and DeepSeek and Last.fm API credentials. The notebook retains its original installation cells; dependency versions are unpinned.

Set credentials in the environment before starting Jupyter:

```bash
export DEEPSEEK_API_KEY="your-deepseek-api-key"
export LASTFM_API_KEY="your-lastfm-api-key"
jupyter notebook music-recommend.ipynb
```

Run the cells in order and interact through the final chat cell. Last.fm results are track-page links; the notebook does not provide audio playback.
