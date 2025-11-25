# **📚 Ollama RAG Manager**

This is a single-file, client-side web application that implements a **Retrieval-Augmented Generation (RAG)** pattern. It allows users to upload local documents and use their content to provide context for a Large Language Model (LLM) running locally via the [Ollama](https://ollama.com/) service.

The entire application runs from a single HTML file, featuring local authentication, persistent storage, and direct communication with your local LLM server.

### **💻 Technologies Used**

| Language/Framework | Type | Role |
| :---- | :---- | :---- |
| **HTML** | Markup | Primary structure, single-file deployment. |
| **JavaScript (ES6)** | Scripting | All application logic, authentication, document handling, and API communication. |
| **Tailwind CSS** | Styling | Utility-first framework for responsive and aesthetic UI. |
| **Ollama** | Runtime | Local LLM server, providing the generation API. |
| **Web Crypto API** | Utility | Secure (or fallback) password hashing for local user accounts. |
| **Local Storage** | Data Persistence | Stores user accounts and uploaded documents persistently in the browser. |

## **✨ Features**

* **Local RAG Implementation:** Use selected documents as context for local LLMs, ensuring grounded responses.  
* **Persistent User Accounts:** Secure local authentication using password hashing, with accounts and documents stored persistently in your browser's Local Storage.  
* **Document Management:** Drag-and-drop text files for easy upload.  
* **Context Control:** Checkbox controls to manually select which documents should be included in the RAG context for any given query.  
* **Token Estimation:** A helpful counter that estimates the token usage of your selected context, helping prevent LLM context window overloads.  
* **Ollama Status Check:** Automatically checks connectivity and lists available models from your running Ollama server.

## **🚀 Prerequisites**

Before running this application, you must have the following running locally:

1. **Ollama:** Download and install the [Ollama service](https://ollama.com/).  
2. **LLM Model:** Pull at least one model, such as Llama 3:  
   ollama pull llama3

## **⚙️ Installation and Setup**

Since this is a single-file application, setup is simple:

1. **Save the File:** Save the provided index.html file to your local computer.  
2. **Configure Ollama:** Ollama requires specific permissions to communicate with your web application. You must run the Ollama service with the OLLAMA\_ORIGINS environment variable set to include your application's source:  
   \# Run Ollama, replacing 8000 with the port you use to serve the file  
   OLLAMA\_ORIGINS="http://localhost:8000" ollama serve

3. **Start a Local Web Server:** You need a local server to serve the index.html file. You can use Python for this:  
   python3 \-m http.server 8000

4. **Access the Application:** Open your browser and navigate to http://localhost:8000.

## **📝 Usage**

### **1\. Sign Up and Login**

Since the application uses browser-based local storage, you must first create an account:

1. Click the **"Sign up"** link at the bottom of the login box.  
2. Create a unique username and password.  
3. Log in using the newly created credentials.

### **2\. Upload Documents**

1. Drag and drop any text-based file (e.g., .txt, .md, .log) into the **"Drag & Drop Text Files"** area.  
2. The content will be saved immediately to your local storage and associated with your user account.

### **3\. Select Context**

1. Documents will appear in the list on the left sidebar.  
2. Use the **checkboxes** next to each document to select which ones you want the LLM to consider when answering your query.  
3. Watch the **Context Stats** counter to monitor estimated token usage and avoid overloading the LLM's context window.

### **4\. Run RAG Query**

1. Select your desired LLM from the model dropdown (e.g., llama3).  
2. Enter your question in the query box.  
3. Click **"Generate Answer."** The application will compile the context from your selected documents and send the complete prompt to Ollama. The response will appear below.

## **💾 Data Persistence**

This application is designed for long-term local use:

* **Users & Documents:** All user profiles and uploaded document contents are stored in your browser's **Local Storage**.  
* **Multi-User Isolation:** When you **Logout**, the application cleans up the active listener, ensuring that when a different user logs in, they only see documents associated with their specific username. Data remains private and isolated.  
* **Note on Local Storage:** Data persists across browser restarts and computer reboots, but will be lost if you clear your browser's site data or use Incognito/Private mode.
* ![Localhost Screenshot](screenshot.png)
