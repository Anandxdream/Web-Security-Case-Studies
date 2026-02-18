# SQL Injection – Login Bypass

## Overview
This lab demonstrates an authentication bypass caused by improper handling of user-supplied input in a login form.

## Vulnerability Type
SQL Injection  
OWASP Top 10 2021 – A03: Injection

## Objective
Gain unauthorized access to the application by manipulating the login query.

## Testing Process

While testing the login functionality, I intercepted the authentication request using Burp Suite. The application accepted username and password parameters without proper validation.

I modified the `username` parameter and injected a basic SQL payload to test for injection behavior.

## Payload Used

' OR 1=1 --

## Result

After forwarding the modified request, the application logged me in without valid credentials.

This indicates that the backend query was likely structured in a way similar to:

SELECT * FROM users WHERE username = '' OR 1=1 --' AND password='...';

The injected condition evaluated to true, bypassing authentication.

## Impact

An attacker can:
- Bypass authentication
- Access restricted areas
- Potentially escalate privileges

## Root Cause

- Unsanitized user input
- Dynamic query construction
- No parameterized statements

## Remediation

- Use prepared statements
- Implement input validation
- Apply least privilege database permissions

