# CS 305 Portfolio: Artemis Financial

# Summarize your client and its software requirements.

Artemis Financial is a financial services company that offers clients savings, retirement, investment, and insurance planning. The company wanted to modernize its web-based software and protect sensitive customer financial data. My job was to assess the security of its Spring Boot RESTful web application and then refactor the code to meet secure software practices, including encrypting data in transit with HTTPS, verifying data integrity with a checksum, and addressing vulnerable third-party dependencies.

# What did you do well, why does secure coding matter, and what value does it add to a company?

I did well at methodically reviewing the code base and its dependencies instead of only looking at the code I could see. I ran the OWASP Dependency-Check tool, read through the flagged CVEs, and sorted them by severity so the most dangerous issues were handled first. Coding securely matters because a single vulnerability can expose customer data, which leads to financial loss, legal trouble, and damaged trust. For a company like Artemis Financial, which handles sensitive financial information, software security protects its reputation, keeps it compliant with regulations, and is far cheaper than cleaning up after a breach.

# Which part of the vulnerability assessment was challenging or helpful?

The most helpful part was learning to read a dependency-check report and tell the difference between a real risk and a false positive. The most challenging part was getting the scan to run reliably, since I hit NVD errors with the plugin even with an API key, and figuring out which findings actually needed a fix versus a suppression. Working through that taught me to troubleshoot tooling instead of giving up on it. [Add one specific example from your own experience here.]

# How did you increase layers of security, and what would you use in the future?

I added layers by enabling HTTPS with a keystore and certificate so data is encrypted in transit, by adding a SHA-256 checksum route so data integrity can be verified, and by updating or suppressing vulnerable dependencies after reviewing them. This follows a defense in depth approach, where no single control is the only thing protecting the application. In the future I would keep using dependency scanning like OWASP Dependency-Check, and I would add static analysis, a threat modeling approach such as STRIDE, and regular manual code review. I would decide on mitigations by weighing severity scores, how exposed the affected component is, and how costly the fix is.

# How did you make sure the code was functional and secure, and how did you check for new vulnerabilities after refactoring?

After each change I ran the application and tested it in the browser to confirm the endpoints still worked, including confirming that the HTTPS connection was trusted and that the /hash route returned the expected SHA-256 value. Then I reran the dependency-check scan and compared the new report to the original to confirm the vulnerabilities I targeted were gone and that my updates had not introduced new ones. Rerunning the scan after every refactor is what keeps a fix from quietly creating a new problem.

# What resources, tools, or coding practices might help in future work?

The tools and practices I expect to reuse are Maven for dependency management, OWASP Dependency-Check for scanning, the Spring Boot documentation, keytool for generating keystores and certificates, and the OWASP guidance on secure coding. Practices that will carry forward include keeping dependencies current, never trusting input, encrypting data in transit, verifying integrity, and testing again after every change.

# What could you show future employers from this assignment?

I would show the [Vulnerability Assessment Report / Practices for Secure Software Report] I included in this repository. It demonstrates that I can analyze an application for weaknesses, explain the risk in plain language to a client, apply concrete fixes, and document the results professionally. It also shows I understand the full cycle of assess, mitigate, and verify, which is exactly what employers look for in secure software work.
