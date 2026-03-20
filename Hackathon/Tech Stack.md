
### . Frontend (The UI)

- **Framework:** **React.js** (easiest ecosystem for JS developers) or **Next.js**.
    
- **Styling:** **Tailwind CSS** (for quickly building the search bar and result cards).
    
- **HTTP Client:** **Axios** or **Fetch API** (to talk to your backend).
    
- **Build Tool:** **Vite** (if using plain React) for fast development.
    

### 2. Backend (The Orchestrator)

- **Runtime:** **Node.js**.
    
- **Framework:** **Express.js** (standard, easy to learn) or **Fastify** (faster, lower overhead).
    
- **Scheduling:** **node-cron** (npm package) to run your "Cron job" scripts for fetching emails periodically.
    

### 3. AI & Search (The Core "RAG" Tech)

- **LLM SDK:** **Azure OpenAI SDK** (part of the `openai` npm package).
    
    - _Usage:_ Connecting to the GPT-4.1 deployment you have access to.
        
- **Vector Database Client:** **@azure/search-documents**.
    
    - _Usage:_ Connecting to Azure AI Search to push/pull vectors.
        
- **Orchestration Library (Optional but Recommended):** **LangChain.js**.
    
    - _Usage:_ It simplifies the "glue" code for RAG (chunking text, managing prompts, switching models).
        

### 4. Data Sources (The Connectors)

- **Gmail:** **googleapis** (official Node.js client for Google APIs).
    
- **Microsoft Outlook:** **@microsoft/microsoft-graph-client** (if you need to fetch Outlook emails).
    

### 5. Infrastructure & Tools

- **Package Manager:** **npm** or **yarn**.
    
- **Environment Management:** **dotenv** (to securely manage your API keys).
    
- **Git:** For version control.