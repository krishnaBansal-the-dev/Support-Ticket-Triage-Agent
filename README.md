# Support Ticket Triage Agent

LangGraph agent that classifies a support ticket, routes it, drafts a reply, reviews it, and sends it. Billing replies wait for a human to approve first.

## Run

1. Put your key in a `.env` file: `GROQ_API_KEY=...`
2. Open `support_ticket_triage_agent.ipynb` and run all cells in order (download the requirements through pip install -r requirements.txt)
3. For the billing ticket it stops and asks you. Type `approve` or type your own reply.

## LLM

  ChatGroq ( model : "openai/gpt-oss-20b" )

## Tricky part

  The retry loop. At first my second ticket on the same thread kept the attempt count from the first one, so it barely got any retries. Resetting the counter in the classify step fixed it.