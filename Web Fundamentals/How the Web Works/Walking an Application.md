🌐 Walking a Web Application — Study Notes
🧭 Task 1: Walking an Application
🔹 Web Application Review
Manual web application analysis identifies security issues missed by automated tools.
Focus is on observing behavior, structure, and exposed components.
🔹 Built-in Browser Tools
View Source → Displays raw client-side code returned from server.
Inspector → Examines and modifies live DOM elements.
Debugger (Sources) → Controls and analyzes JavaScript execution.
Network → Monitors HTTP/HTTPS requests and responses.
🔹 Key Concept
Client-side tools reveal hidden logic, misconfigurations, and sensitive data exposure.
✅ Lab Answer
Answer: Done
🔍 Task 2: Exploring the Website
🔹 Application Mapping
Identify interactive components such as:
Login forms
Input fields
Navigation links
Document:
Pages
Features
User interaction points
🔹 Security Perspective
Entry points often lead to vulnerabilities.
JavaScript and UI elements may expose hidden functionality.
✅ Lab Answer
Answer: Done
📄 Task 3: Viewing Page Source
🔹 Page Source Definition
Raw code sent from server to client.
Includes:
HTML → Structure
CSS → Styling
JavaScript → Interactivity
🔹 Key Elements
📝 Comments
Syntax: <!-- comment -->
Not visible in UI but readable in source.
May expose:
Hidden URLs
Developer notes
Sensitive info
🔗 Anchor Tags
<a href="URL">Link</a>
Defines navigation links.
href attribute stores destination.
📁 External Resources
Included via:
<link>, <script>, <img>
Can reveal directory structures.
🔹 Security Findings
1. Hidden Endpoints
Comments may expose development paths.
2. Directory Listing
Misconfiguration allows file browsing.
Sensitive files (e.g., .txt, backups) may be exposed.
3. Framework Detection
Framework name/version often in comments.
Outdated frameworks → known vulnerabilities.
✅ Lab Answers
Q1: THM{HTML_COMMENTS_ARE_DANGEROUS}
Q2: THM{NOT_A_SECRET_ANYMORE}
Q3: THM{INVALID_DIRECTORY_PERMISSIONS}
Q4: THM{KEEP_YOUR_SOFTWARE_UPDATED}

🧪 Task 4: Developer Tools — Inspector
🔹 Inspector Definition
Displays live DOM after rendering.
Reflects real-time changes from:
CSS
JavaScript
User interaction
🔹 Capabilities
Modify HTML elements dynamically.
Edit CSS properties.
Reveal hidden or blocked content.
🔹 Key Concept: Paywalls
Implemented using CSS/HTML overlays.
Example property:
display: block;
Changing to:
display: none;
Removes blocking element.
🔹 Security Insight
Client-side restrictions are bypassable.
Sensitive content should not rely on frontend protection.
✅ Lab Answer
Flag: THM{NOT_SO_HIDDEN}
🐞 Task 5: Developer Tools — Debugger
🔹 Debugger Definition
Tool for analyzing JavaScript execution.
Named:
Debugger (Firefox/Safari)
Sources (Chrome)
🔹 Key Features
📌 Pretty Print
Reformats minified JavaScript:
{}
⛔ Breakpoints
Pause execution at specific lines.
Allows inspection of runtime behavior.
🔹 JavaScript Behavior
Scripts can:
Modify DOM
Hide/show elements
Execute timed events
🔹 Security Insight
Obfuscated code hides logic but is still reversible.
Breakpoints reveal hidden runtime data.
✅ Lab Answer
Flag: THM{CATCH_ME_IF_YOU_CAN}
🌐 Task 6: Developer Tools — Network
🔹 Network Tab Definition
Tracks all HTTP/HTTPS requests.
Displays:
Requests
Responses
Headers
Payloads
🔹 AJAX Concept
Asynchronous JavaScript and XML
Sends requests without page reload.
Used for:
Forms
Dynamic updates
🔹 Request Monitoring
Observe:
Endpoints (e.g., contact.msg)
Parameters
Response data
🔹 Security Insight
Sensitive data may appear in requests/responses.
Hidden endpoints accessible via direct requests.
✅ Lab Answer
Flag: THM{GOT_AJAX_FLAG}
🔐 Key Security Takeaways
Client-side code is fully visible and modifiable.
Misconfigurations (directory listing, comments) expose sensitive data.
JavaScript obfuscation ≠ security.
Network traffic reveals backend communication.
Always validate and secure on server-side, not frontend.
