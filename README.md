# CS 305 Portfolio: Artemis Financial

# Summarize your client and its software requirements.

Artemis Financial is a financial services company that offers clients savings, retirement, investment, and insurance planning. The company wanted to modernize its web-based software and protect sensitive customer financial data. My task was to assess the security of its Spring Boot RESTful web application and refactor the code to follow secure software practices, including encrypting data in transit with HTTPS, verifying data integrity with a SHA-256 checksum, and addressing vulnerable third-party dependencies.

# What did you do well, why does secure coding matter, and what value does it add to a company?

I did well at methodically reviewing the whole code base, including its dependencies, instead of only the code I wrote or could see. I ran the OWASP Dependency-Check tool, read through the flagged vulnerabilities, and prioritized them by severity so the most dangerous issues were handled first. Coding securely matters because a single vulnerability can expose customer data, which leads to financial loss, legal trouble, and damaged trust. For a company like Artemis Financial that handles sensitive financial information, software security protects its reputation, supports regulatory compliance, and costs far less than recovering from a breach.

# Which part of the vulnerability assessment was challenging or helpful?

The most helpful part was learning to read a dependency-check report and separate real risks from false positives. The most challenging part was getting the scan to run reliably, since I ran into NVD errors from the plugin even after setting up an API key. Working through that taught me to troubleshoot tooling methodically instead of giving up on it, and it showed me how much a security process depends on its tools working correctly.

# How did you increase layers of security, and what would you use in the future?

I added layers by enabling HTTPS with a keystore and certificate so data is encrypted in transit, by adding a checksum route that returns a SHA-256 hash so data integrity can be verified, and by updating or suppressing vulnerable dependencies after reviewing each one. This follows a defense in depth approach, where no single control is the only thing protecting the application. In the future I would keep using dependency scanning with OWASP Dependency-Check, and I would add static analysis, threat modeling with a framework such as STRIDE, and regular manual code review. I would choose mitigations by weighing severity scores, how exposed the affected component is, and how much effort the fix requires.

# How did you make sure the code was functional and secure, and how did you check for new vulnerabilities after refactoring?

After each change I ran the application and tested it in the browser to confirm the endpoints still worked, including confirming that the HTTPS connection loaded and that the checksum route returned the expected SHA-256 value. Then I reran the dependency-check scan and compared the new report to the original to confirm that the vulnerabilities I targeted were gone and that my updates had not introduced new ones. Rerunning the scan after every refactor keeps a fix from quietly creating a new problem.

# What resources, tools, or coding practices might help in future work?

The tools and practices I expect to reuse are Maven for dependency management, OWASP Dependency-Check for scanning, the Spring Boot documentation, keytool for generating keystores and certificates, and OWASP secure coding guidance. The habits that will carry forward are keeping dependencies current, never trusting input, encrypting data in transit, verifying integrity, and retesting after every change.

# What could you show future employers from this assignment?

I would show the Practices for Secure Software Report included in this repository. It demonstrates that I can analyze an application for weaknesses, explain the risks in plain language to a client, apply concrete fixes, and document the results professionally. It also shows I understand the full cycle of assess, mitigate, and verify, which is the core of secure software work.
