**MIDTERM LABORATORY EXAM**   
**ROLES:**

* **MATTHEW VIRATA** \- Database & Backend Engineer  
* **ERNEST SANCHEZ** \- Systems Architect & Prompt Lead  
* **JAN RHODES TAN** \-  Frontend Engineer & QA & Security Engineer

**OUR GITHUB REPOSITORY:**  
[https\://github.com/VyriaEia/mse2-campus-event-management-system](https://github.com/VyriaEia/mse2-campus-event-management-system)

**Applying SQL in TERMINAL:**  
sqlcmd \-S (localdb)\\MSSQLLocalDB \-Q "SELECT name FROM sys.databases"  
sqlcmd \-S (localdb)\\MSSQLLocalDB \-i database/01\_schema.sql

**INSTRUCTION:**  
ASP.NET Core 8 \+ Dapper \+ SQL Server, with a plain HTML/CSS/vanilla JS frontend served by the same app.

\#\# Run it  
1\. Install the .NET 8 SDK and SQL Server Express or LocalDB.  
2\. Create the database: run \`database/01\_schema.sql\`, then \`database/02\_seed.sql\`.  
3\. If you are not using LocalDB, edit \`ConnectionStrings:Default\` in \`backend/CampusEvents.Api/appsettings.json\`.  
4\. Start the app: \`dotnet run \--project backend/CampusEvents.Api\`  
5\. Open the URL printed in the console (login page: \`/login.html\`). Swagger is at \`/swagger\`.

Demo accounts (created on first start): \`student@campus.edu\` / \`Student\#12345\`, \`admin@campus.edu\` / \`Admin\#12345\`.

\`dotnet test backend/CampusEvents.Tests\`

\#\# Layers  
Browser (fetch) → Controllers → Services (Core) → Repositories (Data, Dapper, parameterized SQL) → SQL Server

\#\# Before real use  
\- Move \`Jwt:Key\` out of appsettings (user secrets or environment variable).  
\- Add HTTPS, rate limiting on login, and an account lockout policy.  
\- Add event create/edit for admins (out of scope for this prototype).  
![][image1]

### 

### **AI Architecture Evaluation (4 sentences)**

The AI-generated architecture is realistic for a 3-hour prototype because it is a single ASP.NET Core monolith with static HTML/CSS/vanilla JS, a three-table 3NF schema, and six endpoints, and it avoids the infrastructure the prompt ruled out (microservices, queues, cloud, Redux). Its layered design (Controller → Service → Repository) with interfaces makes the unit tests with mock objects practical, and the unique constraint on (UserId, EventId) plus a SQL-level seat check handles duplicate and overbooked registrations. Its weak points are optimistic time estimates and some overlap between roles: JWT login and role-based authorization may take beginners longer than planned, and the database member is assigned repository classes that belong to the backend's C\# layer. The plan is feasible if the team freezes the schema and API contract early, cuts non-essential features such as event management, and treats the feature freeze as a firm deadline.

\#\# AI Use Disclosure

\*\*Tool used:\*\* Claude (Anthropic), accessed through the Claude chat interface.  
\*\*Date(s) of use:\*\* October 2, 2026

\*\*What AI was used for\*\*  
\- Generating the system design (requirements, architecture, tech stack, API endpoints, work breakdown) from an RCTC prompt (see Task 1 in SUBMISSION.md).  
\- Generating the starter code: SQL Server schema and seed scripts, the ASP.NET Core backend (controllers, services, Dapper repositories, JWT authentication), the HTML/CSS/vanilla JS frontend, and xUnit \+ Moq unit tests.  
\- Generating the Mermaid ERD source and drafts of the evaluation text.

\*\*What AI did NOT do\*\*  
\- AI did not run, compile, or test the code. All build, run, and test verification was done by the team.  
\- AI-generated text was reviewed and edited by the team before submission.

\*\*Human review and verification\*\*  
\- \[Member name\]: reviewed and tested \[frontend / database / backend / QA part\].  
\- Known issues or changes we made to the AI output: \[list here, or write "None"\].

\*\*Responsibility:\*\* The team is responsible for all content in this repository, including any AI-generated portions. Passwords, secrets, and the JWT key in \`appsettings.json\` are development placeholders only.

ERD:
<img width="632" height="407" alt="image" src="https://github.com/user-attachments/assets/0d180e08-02e1-46e7-95dd-f559f790dcc4" />

**TASK 1 SCREENSHOTS:**  

OUTPUT:  

<img width="572" height="535" alt="image" src="https://github.com/user-attachments/assets/35786661-df35-4ef0-9f85-9257f35fa7ef" />

<img width="539" height="668" alt="image" src="https://github.com/user-attachments/assets/3b04040b-bef5-4188-b85d-0b4e30562deb" />

<img width="483" height="668" alt="image" src="https://github.com/user-attachments/assets/db987ced-55fc-4b9c-a9da-47ac03454f99" />

<img width="486" height="665" alt="image" src="https://github.com/user-attachments/assets/2895de27-36ae-4790-b86d-26a9597ed8aa" />

<img width="496" height="501" alt="image" src="https://github.com/user-attachments/assets/9454f8e0-b622-4774-95af-46f2e04b67d6" />

<img width="516" height="404" alt="image" src="https://github.com/user-attachments/assets/2b6b80f2-09a4-4307-bab6-b0f6ba13d61f" />

<img width="360" height="611" alt="image" src="https://github.com/user-attachments/assets/965769f0-a6ef-4774-904b-5ed7ffce9aed" />

<img width="543" height="761" alt="image" src="https://github.com/user-attachments/assets/bf7e2382-c243-4d58-ada5-4b6fbdb506b9" />


OUTPUT:
<img width="574" height="375" alt="image" src="https://github.com/user-attachments/assets/abebbb34-85eb-4652-b09c-aebdf9409d42" />

<img width="574" height="487" alt="image" src="https://github.com/user-attachments/assets/c9b6364a-e465-43cb-948a-b8606ac90c0c" />

<img width="595" height="440" alt="image" src="https://github.com/user-attachments/assets/31810a01-7e73-4efd-8fec-402d929c59c2" />

