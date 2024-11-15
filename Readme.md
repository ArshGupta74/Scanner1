# Code Scanner

## Description 📝

### Code Scanner

Code Scanner is a web application that allows you to scan your codebase for sensitive information or patterns using regular expressions. It provides three main functionalities:

1. GitHub Repository Scanning: Scan public GitHub repositories for specific patterns defined by regular expressions. This can be useful for identifying potential security vulnerabilities or sensitive data leaks in your open-source projects.
<br>
2. Local Directory Scanning: Scan local directories on your machine for specific patterns defined by regular expressions. This can be helpful for auditing your private codebase or identifying issues within your development environment.
<br>
3. Dynamic Scanning: Leverage Splunk's powerful indexing and search capabilities to perform real-time pattern matching across your codebase. This feature enables:
   - Real-time monitoring of code changes and commits
   - Automatic pattern detection using predefined and custom regex patterns
   - Integration with CI/CD pipelines for automated security checks
   - Advanced analytics and reporting through Splunk dashboards
   - Custom alert creation for specific pattern matches
   - Historical analysis of detected patterns and vulnerabilities

### Features

- Regular Expression Matching: Define custom regular expressions to search for patterns like Social Security numbers, credit card numbers, email addresses, or any other desired pattern.
- File Extension Filtering: Specify the file extensions you want to include in the scan, allowing you to focus on specific types of files (e.g., .java, .py, .js).
- GitHub Integration: Seamlessly scan public GitHub repositories by providing the repository owner and name.
- Local Directory Scanning: Scan directories on your local machine by specifying the directory path.
- Dynamic Scanning with Splunk: 
  - Real-time pattern matching
  - Custom alerting mechanisms
  - Advanced visualization and reporting
  - Integration with existing security workflows
  - Automated compliance checking
- User-friendly Interface: The application provides a straightforward user interface for configuring scan parameters and viewing results.
- AI-Powered Pattern Recognition: Utilizes Mistral AI models for intelligent pattern detection and autofill capabilities.
### Getting Started

To get started with Code Scanner, follow these steps:

1. Clone the repository:

```
git clone https://github.com/ayushsingh01042003/Scanner.git
```

2. Install dependencies for the frontend and backend:

Frontend: 
```
cd frontend
```
```
npm install
```
Backend: 
```
cd backend
```
```
npm install
```

3. Set up the required environment variables for the backend:
   - GITHUB_TOKEN
   - MONGO_DB_URI
   - MISTRAL_API_KEY
   - EMAIL
   - EMAIL_PASSWORD
   - JWT_SECRET
   - GOOGLE_CLIENT_ID
   - GOOGLE_CLIENT_SECRET
   - SPLUNK_HOST
   - SPLUNK_PORT
   - SPLUNK_USERNAME
   - SPLUNK_PASSWORD
<br>

4. Start the frontend and backend servers:

Frontend: 
```
npm run dev
```
Backend: 
```
npm run start
```

5. Access the application in your web browser at ```http://localhost:5173``` and the server is hosted at ```http://localhost:3000```.

## Dependencies ⚙️

To install dependencies, run these commands:

For Frontend:
```
npm i @vitejs/plugin-react
npm i eslint
npm i tailwindcss
npm i vite
npm i jspdf
```
For Backend:
```
npm i cors
npm i axios
npm i dotenv
npm i express
npm i octokit
npm install @mistralai/mistralai
```
## Usage ⚒️

The proper usage of this repository involves the following steps:

1. Install dependencies (`npm install`)
2. Set up environment variables in `.env` file: GITHUB_TOKEN, MONGO_DB_URI, EMAIL,EMAIL_PASSWORD, JWT_SECRET, GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET, SPLUNK_HOST, SPLUNK_PORT, SPLUNK_USERNAME, SPLUNK_PASSWORD, MISTRAL_API_KEY.
3. Start the development server (`npm run dev`)
4. Access the application in your browser (usually http://localhost:5173)
5. Enter the GitHub owner, repository name, file extensions, and regular expressions for PII detection
6. Click "Submit" to initiate the scan
7. View the scan results in the formatted JSON response
8. You can generate the report after scanning and then download that generated report in the report section.
9. Build for production using `npm run build`
10. View the logs in the terminal in Backend directory after running the server at http://localhost:3000/

The application provides a user interface for scanning public GitHub repositories for potential PII vulnerabilities based on the specified file extensions and regular expressions.

## Contributors 🧑‍💻

[ayushsingh01042003](https://github.com/ayushsingh01042003/), [MckinellGreen7](https://github.com/MckinellGreen7/), [smk927](https://github.com/smk927/), [Cobalt9000](https://github.com/Cobalt9000/), [ArshGupta74](https://github.com/ArshGupta74/),

## Backend and Frontend installation steps 🪜:

### In the Backend folder:
```
npm i
node server.js

```
### In the Frontend folder:
```
npm i
npm run dev
```

Run these commands in their respective integrated terminals.

## AI Integration

The application now uses Mistral AI for intelligent pattern recognition:
- Utilizes mistral-medium and mistral-small-2402 models
- Provides smart autofill capabilities for regex patterns
- Enhanced PII detection accuracy


## Example Input Templates

i> For /scan-github route
```json
{
  "owner": "ayushsingh01042003",
  "repo": "DSA",
  "regexPairs": {
    "ssn": "\\b\\d{3}-\\d{2}-\\d{4}\\b",
    "creditCard": "\\b\\d{16}\\b",
    "emailAddress": "\\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,}(?:\\.[A-Za-z]{2,})?\\b"
  }
}
```

ii> For /scan-directory route
```json
{
  "directoryPath": "/home/ayush/Progs/Cognizant/codebase",
  "regexPairs": {
    "ssn": "\\b\\d{3}-\\d{2}-\\d{4}\\b",
    "creditCard": "\\b\\d{16}\\b",
    "emailAddress": "\\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,}(?:\\.[A-Za-z]{2,})?\\b"
  }
}
```

iii> The application now supports dynamic scanning through Splunk integration. Here's a reference of the default regex patterns used for dynamic scanning:

```json
{
  "index": "main",
  "fieldRegexPairs": {
    "ssn": "\\d{3}-\\d{2}-\\d{4}",
    "email": "[\\w\\d\\.-]+@[\\w\\d\\.-]+",
    "credit_card": "\\b(?:\\d[ -]*?){13,16}\\b",
    "ip_address": "\\b(?:\\d{1,3}\\.){3}\\d{1,3}\\b",
    "phone": "\\b(?:\\(?\\d{3}\\)?[-.\\s]?|\\d{3}[-.\\s]?)\\d{3}[-.\\s]?\\d{4}\\b",
    "password": "\\bpassword\\s*[:=]\\s*\\S+\\b",
    "cvv": "\\b\\d{3,4}\\b",
    "address": "\\d+\\s[A-Za-z]+\\s[A-Za-z]+",
    "url": "\\bhttps?:\\/\\/[^\\s/$.?#].[^\\s]*\\b",
    "mac_address": "\\b([0-9A-Fa-f]{2}[:-]){5}([0-9A-Fa-f]{2})\\b"
  }
}
```

Note: When entering information in the UI, use single slash (/) instead of double slash (//). Double slash is only for Postman testing because of formatting issues. The application uses Mistral AI models to autopopulate or fill in the UI, and it will not remember or store any regex pairs or patterns (in your clipboard) required for the scanning purpose.