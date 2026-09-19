---
name: gen-mobile-test
description: Create or validate automation_plan.md and generate one Kotlin/JUnit 5 Appium test from one TestOps-style Test Case in this repository. Use when asked to plan, generate or cover one mobile Test Case. Follow the pages-to-actions-to-tests architecture, verified product locators and Allure conventions; never use for API tests, product fixes or open-ended repair.
---

# Generate a mobile test

## Purpose

Create or validate the automation plan, then generate one verified Appium test
from the supplied mobile scenario. Use the Test Case for expected behavior,
the automation plan for design decisions and current repository sources for
implementation facts.

## Required inputs

| Input | Requirement |
|---|---|
| Test Case | One case with preconditions, actions and expected results |
| Plan | Required after the coverage preflight confirms a gap; create or validate `automation_plan.md` from `automation_plan.mobile.md.template` for this Test Case; the lesson 2.3 LMS checker must return `PASSED` before generation in lesson 2.4 |

Use the complete Test Case text supplied by the task. If the task supplies a
case file, read the whole file because its header may define test data. Do not
assume that a case exists under `fixtures/`.

## Coverage preflight

Run this preflight before creating or validating the plan or loading
implementation-specific context:

1. Search current mobile coverage and run the `@DisplayName|@AllureId`
   inventory command from `AGENTS.md`; there is no registry file.
2. Compare the Test Case behavior and expected result with current tests.
3. If current coverage already proves the behavior, or the assigned
   `@AllureId` is occupied, stop. Cite the existing file, class and test method,
   state that no duplicate will be generated and report that no files changed.

A duplicate-coverage stop does not require an automation plan. When the
preflight confirms a coverage gap, read the required context and create or
validate the plan before changing test code.

## Required context

`AGENTS.md` is already loaded; use its repository rules and source-routing
table without reading the file again. Before planning or editing, read:

1. `AI_POLICY.md`;
2. `agent_docs/test_architecture.md`;
3. `agent_docs/page_object_model.md`;
4. `agent_docs/building_the_project.md`;
5. `appium-tests/README.md`;
6. `baseline_report.md` when present;
7. the nearest test and every page, action, locator and test-data file cited
   by the plan.

Use these sources for layer ownership, locator policy, start state, test
metadata, waits, formatting and execution commands. Keep those rules in their
source documents; do not restate them in this skill.

## Plan creation and validation

Use `automation_plan.mobile.md.template` as the required schema. Preserve its
sections and limits; replace every placeholder and remove unused rows.

1. Create `automation_plan.md` when missing. If an existing plan describes
   another Test Case, replace it only when the request authorizes replacement.
2. Validate the preconditions, test data, step-to-action mapping, locators,
   observable expected results, repository citations, allowed files, stop
   conditions and runner command against the supplied case and current sources.
   Correct a stale claim only when the evidence supports one unambiguous
   replacement. If evidence is missing or conflicting, report the unresolved
   item and stop before test-code changes.
3. Leave a complete plan for the lesson 2.3 LMS checker. Do not write the
   checker's verdict or claim that source validation replaces its `PASSED`
   result. The lesson handoff must supply that result before lesson 2.4
   generation; a revised plan requires another checker pass.

For a planning-only request, stop after creating or validating the plan without
changing test code or running tests. For a read-only request, report the
assessment without changing files. Generate only within the validated plan's
file scope; do not redesign, split or relabel the scenario.

## Pre-generation checks

1. Verify plan citations against the nearest test, pages, actions, locators
   and test data.
2. Read product UI code only to confirm existing testTags.
3. Confirm that every planned file is permitted by the validated plan and
   repository policy.
4. Apply the assertion rules below.

Use the `@AllureId` assigned by the Test Case and verify that it is not already
present. Do not invent or remap the ID during generation.

Stop before test-code changes when any condition applies:

- the plan remains incomplete or inconsistent with the Test Case after validation,
  or the required LMS checker result is missing or failed;
- the plan relies on an existing repository path, symbol, locator or value
  that current sources do not support;
- the Test Case combines behaviors that require separate scenarios;
- the oracle can pass on pre-existing or adjacent UI state;

Return the finding to the plan owner. Do not redesign, split or relabel the
scenario during generation.

The validated plan may introduce a new action-layer method or wait condition
when the Test Case requires it, current sources contain no equivalent and the
change stays within the validated test-layer files. Never invent a product
locator. A locator for an existing UI element must use its verified current
product `testTag`. A locator used only to assert that a removed element stays
absent must be explicitly required by the validated plan and supported by the
repository's migration contract.

## Assertion rules

- Map every assertion to one validated expected result.
- Assert exact copy or test-data identity only when the Test Case requires it.
- Use an observable result that fails when the behavior named in the title
  breaks.
- Do not add adjacent-content checks from an existing test.
- Keep expected values independent from the system under test.

## Verification and result

1. Delegate execution to `run-appium-suite`.
2. Run the generated class through the repository runner when the current OS
   runner supports a class filter. If it does not, use the unfiltered runner
   and verify that the generated test executed.
3. Require a fresh result for the generated Test Case with zero failures and
   errors. Do not require a fixed full-suite total for this one-test task.
4. Run the repository formatting check for changed Kotlin.

On success, report the Test Case ID, changed files, assertions, command and
observed result for the generated test. On failure, report the smallest
relevant evidence and stop. Test
repair and product modification require separate authorization.
