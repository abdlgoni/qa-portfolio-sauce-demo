# Manual QA Testing Portfolio

## Overview

This repository contains my manual QA testing portfolio focused on
authentication-related features (Registration & Login) of a public
e-commerce demo website.

The purpose of this project is to demonstrate my QA mindset, test design
approach, and ability to identify functional, usability, and basic
security risks.

## Scope

- Registration form testing
- Login functionality testing
- Validation behavior
- Usability and UX observations
- Basic security input validation (non-intrusive)

## Out of Scope

- Automated testing
- Load or stress testing
- Penetration testing
- Source code review

## Repository Structure
qa-portfolio-sauce-demo/
├── test-cases/
│   ├── TC_Registration.md
│   └── TC_Login.md
│
├── ux-reports/
│   ├── UX-001_Registration_Data_Retention.md
│   └── UX-002_Login_Data_Retention.md
│
├── test-summary/
│   └── Login_test_summary.md
│
└── README.md
## Test Artifacts

### Test Cases

- Registration test cases (positive & negative scenarios)
- Login test cases including validation, usability, and session handling

### Bug & Improvement Reports

- Password strength validation improvement
- Login email field retention usability issue

### Test Summary

- Login module summary including observations and improvement areas

## Testing Approach

- Requirement-agnostic testing (black-box)
- Separation of functional validation and UX improvements
- Industry best practices used as reference when no PRD is available

## Environment

- Website: Sauce Demo (Shopify-based demo site)
- Browser: Chrome
- OS: Windows 11

## Notes

All findings are based on observed system behavior.
No intrusive or destructive testing was performed.

Created as part of a personal QA learning and portfolio project.
