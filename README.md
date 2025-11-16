Cloudflare AI Chat Agent – Custom Build

This project is an AI-powered chat agent built on the Cloudflare Agents Platform.
It uses Cloudflare Workers, Realtime chat UI, durable state, and an LLM backend to provide a fully interactive assistant.

This repository is based on Cloudflare’s official agents-starter, but I have made several custom modifications described below.

What I Built / Custom Changes
1. Custom AI System Prompt: I modified the agent’s behavior in server.ts to create a Cloudflare-focused assistant.
My version now:
a. Explains Cloudflare concepts (DNS, CDN, WARP, Workers, caching, security)
b. Answers technical questions in simple language
c. Avoids default scheduling/task-focused behavior
d. Provides practical Internet examples

2. Customized UI Welcome Screen

I updated the initial empty-state UI in app.tsx:
a. Added a personalized welcome message
b. Replaced generic suggestions with:
c. Weather/time queries
d. Simple explanations
e. Help drafting messages

3. Added Safer Message Cleanup Logic: Integrated message-cleanup and tool-handling improvements to avoid malformed tool calls.

4. Configured Local + Production Secrets: .dev.vars is ignored for security


5. General Cloudflare Agent Flow Integration: Ensured proper routing with-
a. routeAgentRequest()
b. Realtime streaming
c. Tool integration via tools.ts

This keeps the full agent workflow functional on Cloudflare.

How to Run the Project
1. Install dependencies
npm install

2. Add your API key
Create a .dev.vars file (not committed): OPENAI_API_KEY=your_key_here

3. Start locally
npm start

4. Deploy
npm run deploy

Project Structure
src/
  app.tsx        - UI with custom welcome screen
  server.ts      - Custom system prompt + agent logic
  tools.ts       - Tool definitions
  utils.ts       - Message cleanup + helpers
