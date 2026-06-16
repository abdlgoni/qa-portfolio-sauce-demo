## UX IMPROVEMENT REPORT 002

## Login Form – Email Field Retention Enhancement

## REPORT OVERVIEW

- **Report ID:** UX-002
- **Module:** User Authentication – Login
- **Category:** Usability / UX Improvement
- **Priority:** MEDIUM
- **Impact Area:** User Experience & Efficiency
- **Status:** RECOMMENDED
- **Reported By:** Abdul Goni
- **Date:** December 29, 2025
- **Related Test Cases:**
  - TC-LOG-002 – Invalid password
  - TC-LOG-003 – Unregistered email
  - TC-LOG-005 – Empty password
  - TC-LOG-008 – Malformed email (server-side validation)

## EXECUTIVE SUMMARY

The login form currently clears **both email and password fields** after a failed authentication attempt.  
While this behavior is functionally correct and secure, it introduces unnecessary friction by forcing users to re-enter non-sensitive data that is usually already correct.

**Recommendation:**  
Retain the email field value and clear only the password field after login failure.

**Expected Outcome:**

- Faster error recovery
- Reduced user frustration
- Alignment with industry UX standards

## CURRENT SYSTEM BEHAVIOR

**Functional Status:** WORKING AS DESIGNED

The system correctly performs the following:

- Validates login credentials
- Displays error message: _“Incorrect email or password”_
- Keeps user on the login page
- Prevents unauthorized access
- Maintains application stability

There are **no functional defects** or system errors observed.

## CURRENT USER FLOW (FAILED LOGIN)

1. User enters email (e.g. `john@example.com`)
2. User enters incorrect password
3. User clicks **SIGN IN**
4. Error message displayed
5. **Email field is cleared**
6. **Password field is cleared**
7. User must re-enter both fields
8. User retries login

## UX ISSUES IDENTIFIED

### 1. Unnecessary Data Re-entry

- Email is commonly correct during failed attempts
- Clearing it adds avoidable typing effort
- Especially frustrating on mobile devices

### 2. Reduced Error Clarity

- Error message is generic
- Clearing the email prevents users from visually confirming which input was incorrect

### 3. Increased Cognitive Load

- Users must remember and retype known-correct data
- Slows down the login recovery process

### 4. Deviation from Industry Standards

Most major platforms retain email and clear only password:

- Gmail
- Facebook
- Amazon
- Twitter / X

## AFFECTED SCENARIOS

- Wrong password entered
- Empty password submission
- Unregistered email
- Server-side email validation failure

All scenarios exhibit the **same clearing behavior**, regardless of which input is actually invalid.

## PROPOSED IMPROVEMENT

### Recommended Behavior (After Failed Login)

1. Error message displayed
2. **Email field retained**
3. **Password field cleared**
4. Cursor focus returns to password field
5. User can immediately retry password

### Field Handling Recommendation

- **Email:** RETAIN (non-sensitive data)
- **Password:** CLEAR (security-sensitive data)
- **Focus:** Password field

## BUSINESS & UX IMPACT

### User Experience Benefits

- Faster retry flow
- Reduced frustration
- Clearer error recovery path

### Estimated Impact

- Saves ~10–15 seconds per failed login attempt
- Reduces login abandonment risk
- Improves perceived product quality

### Development Consideration

- Low implementation effort
- Non-breaking change
- Minimal risk

## SUSPECTED ROOT CAUSE

- Global `form.reset()` triggered on all validation errors
- No selective field retention logic applied

## RECOMMENDATION SUMMARY

1. Retain email field value after failed login
2. Clear password field only
3. Maintain current security behavior
4. Align UX with industry best practices

## OUT OF SCOPE

- Changing authentication logic
- Modifying error message wording
- Backend security or validation rules

## RELATED FINDINGS

- Similar UX issue identified in Registration flow (TC-REG-004)
- Indicates potential system-wide form handling pattern

This report documents a usability enhancement opportunity discovered during manual QA testing.  
The system functions correctly, but the proposed change improves efficiency, clarity, and user satisfaction without compromising security.
