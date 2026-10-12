# Conversational Multi-Agent Music Recommender

A personal high-school project exploring mood-aware music recommendations through collaborative LLM agents, conversational context, structured review, and external tools.

## Core idea

Music discovery starts with understanding the listener. Socratic-style conversation uncovers mood and musical preferences. A profile builder and a separate critic refine that context before a recommender selects tracks and retrieves Last.fm links.

```text
Conversation → Profile Builder ↔ Profile Critic → Recommendations → Link Retrieval
```

## What makes the design forward-looking

- **Specialized agents:** Conversation, profiling, review, recommendation, and tool execution have distinct responsibilities.
- **A critique-and-refine loop:** A separate agent reviews the profile, accounting for how much information the user supplied.
- **Contextual personalization:** Recommendations consider both musical taste and the listener's current emotional state, using conversation rather than requiring a listening-history dataset.
- **Adaptive orchestration:** An LLM-based router directs requests, profile revisions, and unavailable-link feedback to the appropriate agent.
- **Tool-backed discovery:** A name-normalization agent handles Chinese and English track metadata; a registered function searches Last.fm for track-page links.

Together, these choices demonstrate an agent-orchestration approach to personalized discovery. This is an exploratory prototype; recommendation quality has not been benchmarked.

## Run

Requires Python, Jupyter, AutoGen/AG2, the OpenAI client, `requests`, and DeepSeek and Last.fm API credentials. The notebook retains its original installation cells; dependency versions are unpinned.

Set credentials in the environment before starting Jupyter:

```bash
export DEEPSEEK_API_KEY="your-deepseek-api-key"
export LASTFM_API_KEY="your-lastfm-api-key"
jupyter notebook music-recommend.ipynb
```

Run the cells in order and interact through the final chat cell. Last.fm results are track-page links; the notebook does not provide audio playback.

## Project history

The high-school prototype is preserved with its original workflow. The October 2026 archive pass standardized English prompts, comments, and identifiers, and moved credentials to environment variables. See [MAINTENANCE.md](MAINTENANCE.md) and the commit history for the recorded maintenance work.
