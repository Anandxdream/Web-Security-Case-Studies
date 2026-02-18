# SQL Injection – Authentication Bypass

## Vulnerability Type
SQL Injection (OWASP A03:2021 - Injection)

## Objective
Bypass login authentication using SQL payload.

## Steps to Reproduce
1. Intercept login request using Burp Suite.
2. Identify vulnerable parameter (username field).
3. Inject SQL payload.

## Payload Used
' OR 1=1 --

## Impact
Attacker can bypass authentication and gain unauthorized access.

## Root Cause
Improper input validation and unsanitized user input.

## Mitigation
- Use parameterized queries (Prepared Statements)
- Input validation
- Use ORM frameworks
