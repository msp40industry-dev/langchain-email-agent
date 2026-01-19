# 📧 Email Agent with Human-in-the-Loop

AI email assistant with authentication, dynamic middleware, and human approval for critical actions using LangChain.

Part of LangChain Academy Foundation Course - EBIS Business Techschool

## 📋 Description

Email Agent is an AI assistant that manages emails with different access levels based on user authentication. It demonstrates advanced LangChain concepts including stateful agents, dynamic middleware, and human-in-the-loop patterns.

## 🎯 Features

* **Dynamic Authentication**: Tools available change based on authentication state
* **Smart Inbox Management**: Check and analyze incoming emails
* **Draft Generation**: AI-powered email response suggestions
* **Human Approval**: Review and edit emails before sending
* **Dynamic Middleware**: System prompts and tools adapt to user state
* **Secure Context**: Credentials managed through EmailContext schema

## 🏗️ Architecture
```
User Request
   ↓
Agent (unauthenticated)
   ↓
Authenticate Tool → Updates State
   ↓
Agent (authenticated) → New tools available
   ↓
Check Inbox → Read emails
   ↓
Generate Draft Response
   ↓
Human-in-the-Loop → User reviews/edits
   ↓
Send Email (after approval)
```

## 🛠️ Tech Stack

- **LangChain**: Agent framework
- **LangGraph**: State management and orchestration
- **OpenAI GPT-5-nano**: Language model
- **AgentChat**: Open-source chat UI (agentchat.vercel.app)
- **Python 3.8+**

## 🚀 Usage

Check the `email_agent.py` file for the complete implementation.

### With AgentChat UI

1. Run the agent locally (default: `http://localhost:2024`)
2. Go to [agentchat.vercel.app](https://agentchat.vercel.app)
3. Enter deployment URL and agent ID
4. Start chatting!

## 🔧 Core Components

### State Schema

Tracks authentication status to control tool access.

### Context Schema

Securely stores user credentials for authentication.

### Tools

**authenticate(email, password)**
- Validates user credentials
- Updates authentication state

**check_inbox()**
- Retrieves recent emails
- Only available after authentication

**send_email(to, subject, body)**
- Sends email response
- Requires human approval

### Middleware

**dynamic_tool_call**
- Exposes different tools based on authentication state
- Unauthenticated: only `authenticate`
- Authenticated: `check_inbox` and `send_email`

**dynamic_prompt_func**
- Changes system prompt based on state
- Guides agent behavior appropriately

**HumanInTheLoopMiddleware**
- Interrupts before critical actions
- `authenticate`: No interrupt (automatic)
- `check_inbox`: No interrupt (automatic)
- `send_email`: Interrupt for human approval ✋

## 💡 Key Concepts Learned

✓ **Stateful Agents**: Managing authentication state across interactions
✓ **Dynamic Middleware**: Adapting tools and prompts based on state
✓ **Human-in-the-Loop**: Requiring approval for sensitive operations
✓ **Context Management**: Secure handling of credentials
✓ **Tool Runtime**: Accessing context within tool execution

## 📊 Flow Example

1. **User**: "I would like to check my inbox"
2. **Agent**: Requests email and password
3. **User**: Provides credentials
4. **Agent**: Authenticates → Updates state
5. **Agent**: Checks inbox → Shows email from Jane
6. **Agent**: Suggests 2 draft responses
7. **User**: Selects draft or writes custom response
8. **Agent**: Requests approval to send
9. **User**: Reviews/edits in AgentChat UI
10. **Agent**: Sends email after approval

## 🌐 AgentChat Integration

AgentChat provides:
- Clean chat interface
- Built-in email editor
- Easy draft review and modification
- Visual tool call tracking
- Thread management

Simply deploy your agent and connect via the AgentChat web app.

## 📁 Project Structure
```
email-agent-langchain/
├── email_agent.py           # Main agent implementation
├── requirements.txt         # Dependencies
├── .env.example            # Environment variables template
├── .gitignore
└── README.md
```

## 🔜 Potential Improvements

- [ ] Add calendar integration for meeting scheduling
- [ ] Implement email categorization/prioritization
- [ ] Support multiple email accounts
- [ ] Add search functionality for past emails
- [ ] Implement draft saving for later
- [ ] Multi-language support
- [ ] Email templates library

## 📚 References

- [LangChain Documentation](https://python.langchain.com/)
- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [AgentChat](https://agentchat.vercel.app)
- [LangChain Academy](https://academy.langchain.com/)

## 📄 License

MIT License

## 👨‍💻 Author

Miguel - Master's in Generative AI Engineering @ EBIS Business Techschool

[LinkedIn](tu-perfil-linkedin) | [GitHub](tu-perfil-github)

---

⭐ If you find this project useful, give it a star on GitHub!
