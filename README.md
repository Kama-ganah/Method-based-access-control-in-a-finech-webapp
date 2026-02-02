# Overview
During an assessment of the application’s administrative functionality, I identified a high-severity access control vulnerability stemming from reliance on HTTP methods for privilege enforcement. The system restricted administrative actions based on request methods (e.g., POST), but failed to enforce the same checks for alternate methods such as GET. By manipulating the HTTP method, a non-privileged user was able to bypass access restrictions and escalate their privileges to administrator.

# Methodology

Step 1: Logged in as both admin and non-admin users to understand normal access restrictions.

Step 2: Captured requests to the admin panel using Burp Suite and observed method-based enforcement.

Step 3: Intercepted a restricted request and replayed it with the original method (POST) to confirm access denial.

Step 4: Modified the request method to GET and replayed the request as a non-admin user.

Step 5: Confirmed successful execution of administrative actions, including promotion of a user to administrator.

# Conclusion

This assessment confirmed a critical access control bypass via method tampering. The flaw allows attackers to escalate privileges and perform sensitive administrative operations by exploiting the system’s reliance on HTTP methods. Proper, method-independent server-side authorization checks are essential to secure administrative endpoints and prevent privilege escalation.
