# Enspct - Build Request Type Form (UC-3.2) Test Report

**Project:** Enspct Inspection Platform
**Module:** Build Request Type Form
**Environment:** https://testbravo.enspct.com:7100
**Tester:** Automated via Playwright MCP

---

## Test Results Summary

| # | Test Case ID | Title | Status | Date | Notes |
|---|-------------|-------|--------|------|-------|
| 1 | TC-3.2-F01 (179123) | Should display form builder with Location and Entity static fields | PASS | 2026-03-26 | Entity (المنشأة) and Location (الموقع) both visible on Form Builder |
| 2 | 179124 | Check to save request form with any invalid controls | PASS | 2026-03-26 | Error "The Form has invalid controls" displayed correctly |

---

## Detailed Results

### 1. TC-3.2-F01: Should display form builder with Location and Entity static fields
- **Work Item ID:** 179123
- **Status:** PASS
- **Date:** 2026-03-26
- **Login Role:** Admin

**Steps Executed:**
1. Navigate to Request Types list — **Done** (Builders > Request Types)
2. Click 'Build Form' on a request type row — **Done** (clicked on "devrequest")
3. System displays the Form Builder page — **Verified**

**Expected:** Form Builder displays with two static fields pre-added: Location (Map field) and Entity (Dropdown list field).
**Actual:** Form Builder displayed with both static fields:
- المنشأة (Entity) — Dropdown list field — **Visible**
- الموقع (Location) — Map field — **Visible**

**Screenshots:**
- `screenshots/step1-request-types-list.png`
- `screenshots/step2-form-builder.png`
- `screenshots/step3-verification.png`

---

### 2. 179124: Check to save request (or create new version) form with any invalid controls
- **Work Item ID:** 179124
- **Status:** PASS
- **Date:** 2026-03-26
- **Login Role:** Admin

**Steps Executed:**
1. Navigate to Request Types list — **Done** (Builders > Request Types)
2. Click 'Build Form' on a request type row — **Done** (clicked on "devrequest")
3. System displays the Form Builder page — **Verified**
4. Drag and drop Dropdown field, then clear the option text to create invalid data — **Done** (expanded sidebar palette, dragged Dropdown, cleared option label)
5. Press Save button — **Done**

**Expected:** Error displayed: "The form has invalid controls."
**Actual:** Alert dialog displayed with message: **"The Form has invalid controls"** — Dropdown field highlighted in red as invalid.

**Screenshots:**
- `screenshots/tc2-sidebar-expanded.png`
- `screenshots/tc2-179124-invalid-controls-error.png`

---
