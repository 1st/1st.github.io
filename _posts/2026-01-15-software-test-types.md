---
title: Software Test Types
category: testing
tags:
  - Guide
---

Testing is a cornerstone of modern software development, ensuring that applications work as intended, remain reliable, and deliver a smooth user experience. Without proper testing, small coding mistakes can slip into production, leading to bugs, security vulnerabilities, performance issues, or even complete system failures.

By running different types of tests, teams can catch problems early, verify that new features do not break existing ones, and confirm the software meets business and user expectations. In short, testing is not just about finding defects -- it is about building confidence in the quality of the product before it reaches the hands of real users.

## 1. By Scope (How much of the system is tested)

| Test Type                 | What It Does                                                                   | Analogy                                                  |
| ------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------- |
| **Unit Test**             | Tests **one small piece** of code (a function, method, or class) in isolation. | Checking if one Lego block is strong enough.             |
| **Integration Test**      | Tests **how different modules/components work together**.                      | Seeing if two Lego blocks connect properly.              |
| **System Test**           | Tests the **entire application** as a whole.                                   | Playing with the full Lego set after building it.        |
| **End-to-End (E2E) Test** | Simulates **real user flows** from start to finish, often through the UI.      | Pretending to be the customer playing with the Lego set. |

---

## 2. By Purpose (Why you are running the test)

| Test Type              | What It Does                                                                    | Analogy                                                             |
| ---------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Smoke Test**         | Quick check to see if the system basically works after changes.                 | Turning on the Lego train to see if it runs at all.                 |
| **Sanity Test**        | Narrow check to verify a **specific new change** works (less broad than smoke). | Checking if a new Lego motor works before assembling everything.    |
| **Regression Test**    | Ensures **old features still work** after changes.                              | Making sure your Lego car still moves after adding new decorations. |
| **Performance Test**   | Measures **speed, responsiveness, and stability** under load.                   | Seeing if your Lego bridge can hold 10 cars at once.                |
| **Load / Stress Test** | Tests **how the system behaves under heavy use** or extreme conditions.         | Putting 50 Lego trains on one track to see when it breaks.          |
| **Security Test**      | Checks for vulnerabilities and weaknesses.                                      | Making sure nobody can steal your Lego without you noticing.        |
| **Usability Test**     | Measures how easy it is for users to use the system.                            | Asking friends if they can build the Lego set without instructions. |

---

## 3. By Approach (How tests are written and executed)

| Test Type                             | What It Does                                                                                 | Analogy                                                        |
| ------------------------------------- | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| **TDD (Test-Driven Development)**     | Write **tests first**, then write code to pass those tests.                                  | Designing a Lego challenge before you start building.          |
| **BDD (Behavior-Driven Development)** | Write tests in **plain language** (often using Given-When-Then format) to describe behavior. | Agreeing with friends what the Lego should do before building. |
| **Manual Testing**                    | Human testers click, type, or use the app to find issues.                                    | You play with the Lego yourself.                               |
| **Automated Testing**                 | Scripts and programs run tests automatically.                                                | A robot builds and tests the Lego set for you.                 |

---

## 4. Special Types

| Test Type              | What It Does                                                                   | Analogy                                                   |
| ---------------------- | ------------------------------------------------------------------------------ | --------------------------------------------------------- |
| **Acceptance Test**    | Confirms the system meets **business requirements** (often done with clients). | Checking if the Lego set matches the picture on the box.  |
| **Exploratory Test**   | Tester freely explores without a strict plan to find issues.                   | Just playing around with the Lego set to see what breaks. |
| **Compatibility Test** | Checks if the system works on **different devices, OS, browsers**.             | Seeing if the Lego car runs on all kinds of tracks.       |

---

Tip for remembering:

* **Scope** = How big the test is (unit -> integration -> system -> E2E)
* **Purpose** = Why you are running it (smoke, regression, performance, security...)
* **Approach** = How you write/run it (TDD, BDD, manual, automated)

## Software Test Types (visual mind map)

```sql
Software Test Types
|
|- By Scope
|   |- Unit Test "(Small piece of code)"
|   |- Integration Test "(Modules working together)"
|   |- System Test "(Entire application)"
|   |- End-to-End Test "(User flow from start to finish)"
|
|- By Purpose
|   |- Smoke Test "(Quick overall check)"
|   |- Sanity Test "(Check specific fix)"
|   |- Regression Test "(Ensure old features still work)"
|   |- Performance Test "(Measure speed and stability)"
|   |- Load / Stress Test "(Test under heavy use or extreme load)"
|   |- Security Test "(Vulnerability check)"
|   |- Usability Test "(User-friendliness)"
|
|- By Approach
|   |- TDD (Test-Driven Development) "(Write tests first, then code)"
|   |- BDD (Behavior-Driven Development) "(Plain language scenarios)"
|   |- Manual Testing "(Human tester executes tests)"
|   |- Automated Testing "(Scripts run tests automatically)"
|
|- Special Types
    |- Acceptance Test "(Meets business requirements)"
    |- Exploratory Test "(Freeform testing)"
    |- Compatibility Test "(Works across Devices/Browsers)"
```
