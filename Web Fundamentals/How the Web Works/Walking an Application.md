🌐 Walking a Web Application — Detailed Study Notes
🧭 Task 1: Walking an Application
🔹 Web Application Security Review
Manual analysis involves systematically interacting with a web application to identify logic flaws, misconfigurations, and exposed functionality that automated tools often overlook.
Focus is on understanding how the application behaves from a user and attacker perspective.
🔹 Core Browser Tools (Client-Side Analysis)
View Source
Displays static HTML returned from server before runtime modifications.
Inspector (DOM Viewer)
Shows rendered DOM, reflecting real-time changes after JavaScript execution.
Debugger (Sources Panel)
Allows inspection and control of JavaScript execution flow.
Network Tab
Captures all HTTP/HTTPS requests and responses, including headers and payloads.
🔹 Key Concepts
Web applications rely heavily on client-server architecture.
Browser tools expose:
Application structure
Hidden endpoints
Client-side logic
Manual enumeration increases attack surface visibility.
🔹 Security Practices
Never trust client-side controls.
Always validate logic server-side.
Minimize exposure of unnecessary resources.
✅ Lab Answer
Answer: Done
🔍 Task 2: Exploring the Website
🔹 Application Mapping (Recon Phase)
Process of identifying:
Pages (routes/endpoints)
Features (forms, dashboards)
Functional components (authentication, search)
🔹 Interactive Elements
Key areas of interest:
Input fields (data entry points)
Buttons (trigger actions)
Forms (data submission mechanisms)
These represent potential attack vectors.
🔹 JavaScript Analysis
JavaScript may:
Handle validation
Control navigation
Call hidden APIs
Client-side scripts often expose:
Hidden endpoints
Business logic
🔹 Key Concepts
Entry points = potential vulnerabilities.
Mapping improves understanding of:
Application flow
User roles
Access control boundaries
🔹 Security Practices
Identify all accessible routes.
Track user input flow.
Note authentication requirements.
✅ Lab Answer
Answer: Done
📄 Task 3: Viewing Page Source
🔹 Page Source Definition
Static response returned by server containing:
HTML (structure)
CSS (presentation)
JavaScript (behavior)
🔹 HTML Structure
<html>
  <head></head>
  <body></body>
</html>
🔹 Comments (Information Disclosure)
<!-- hidden information -->
Used for developer notes.
Not rendered in UI.
May expose:
Hidden paths
Debug info
Temporary features
🔹 Hyperlinks (Navigation)
<a href="/path">Link</a>
Defines internal/external navigation.
href reveals accessible endpoints.
🔹 Resource Inclusion
<link rel="stylesheet" href="style.css">
<script src="script.js"></script>
<img src="image.png">
Reveals directory structure and file organization.
🔹 Security Findings
🟠 Hidden Paths
Comments and links may reveal:
Admin panels
Development endpoints
🟠 Directory Listing
Occurs when server allows directory browsing.
Indicates misconfigured permissions.
Can expose:
Backup files
Config files
Sensitive data
🟠 Framework Identification
Framework = reusable codebase for web development.
Often disclosed in:
Comments
Metadata
Version info enables:
Vulnerability lookup
Exploit targeting
🔹 Security Practices
Disable directory listing.
Remove sensitive comments.
Keep frameworks updated.
Restrict access to internal resources.
✅ Lab Answers
Q1: THM{HTML_COMMENTS_ARE_DANGEROUS}
Q2: THM{NOT_A_SECRET_ANYMORE}
Q3: THM{INVALID_DIRECTORY_PERMISSIONS}
Q4: THM{KEEP_YOUR_SOFTWARE_UPDATED}

🧪 Task 4: Developer Tools — Inspector
🔹 Inspector (DOM Analysis Tool)
Displays live DOM tree after rendering.
Reflects:
JavaScript modifications
CSS styling
Dynamic content changes
🔹 DOM vs Source
Page Source → Original HTML
DOM (Inspector) → Modified runtime structure
🔹 Element Manipulation
Modify attributes:
<div class="blocker"></div>
Modify styles:
display: none;
visibility: hidden;
🔹 Paywall Mechanism
Implemented using overlay elements.
Controlled via CSS properties:
display: block;
Removing/changing property reveals hidden content.
🔹 Key Concepts
DOM is fully controllable by user.
Frontend restrictions are not secure controls.
🔹 Security Practices
Enforce access control server-side.
Do not rely on CSS/JS for protection.
Avoid exposing sensitive content in DOM.
✅ Lab Answer
Flag: THM{NOT_SO_HIDDEN}
🐞 Task 5: Developer Tools — Debugger
🔹 Debugger (JavaScript Analysis)
Tool for analyzing execution of scripts.
Enables:
Code tracing
Runtime inspection
Execution control
🔹 Minified & Obfuscated Code
Minified
Removes whitespace to reduce size.
Obfuscated
Alters readability to hide logic.
🔹 Pretty Print
{}
Restores formatting for readability.
🔹 Breakpoints
Pause execution at specific lines.
Allows inspection of:
Variables
DOM state
Execution flow
🔹 JavaScript Execution Flow
Scripts can:
Modify elements dynamically
Remove or hide content
Trigger timed actions
🔹 Key Concepts
Execution can be controlled by user.
Hidden behaviors become observable.
🔹 Security Practices
Avoid embedding sensitive logic client-side.
Minification is not a security control.
Validate all logic server-side.
✅ Lab Answer
Flag: THM{CATCH_ME_IF_YOU_CAN}
🌐 Task 6: Developer Tools — Network
🔹 Network Tab (Traffic Analysis)
Monitors all requests between client and server.
🔹 HTTP Request Structure
GET /endpoint HTTP/1.1
Host: example.com
🔹 HTTP Methods
GET → Retrieve data
POST → Submit data
PUT/PATCH → Update data
DELETE → Remove data
🔹 AJAX (Asynchronous Requests)
Allows background communication without page reload.
Used for:
Form submission
Dynamic updates
🔹 Request Analysis
Inspect:
URL endpoints
Request payload
Response data
🔹 Key Concepts
Hidden endpoints visible via network traffic.
Client-server communication is transparent.
🔹 Security Practices
Validate all input server-side.
Avoid exposing sensitive data in responses.
Use proper authentication and authorization.
✅ Lab Answer
Flag: THM{GOT_AJAX_FLAG}
🔐 Consolidated Security Concepts
🔹 Client-Side Exposure
All frontend code is visible and modifiable.
🔹 Misconfiguration Risks
Directory listing
Exposed files
Improper permissions
🔹 Information Disclosure
Comments
Hidden links
Framework versions
🔹 JavaScript Risks
Obfuscation ≠ security
Logic exposure
🔹 Network Visibility
Requests reveal backend structure.
AJAX exposes hidden endpoints.
🧠 Exam Key Points
Page Source ≠ DOM
Inspector modifies client-side only
Breakpoints control JavaScript execution
Network tab reveals backend communication
Security must be enforced server-side only
