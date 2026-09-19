# Week 2 Kotlin QA course assets

Install this package before the Module 2 test-generation exercises. Copy its
contents into the same directory as `AGENTS.md`.

## Required layout

```text
repository/
├── .agents/
│   └── skills/
│       ├── gen-api-test/
│       │   └── SKILL.md
│       └── gen-mobile-test/
│           └── SKILL.md
├── automation_plan.api.md.template
└── automation_plan.mobile.md.template
```

Preserve these paths and file names. If `.agents/skills/` already exists,
merge the two skill directories without replacing unrelated skills.

Use a practice revision that includes the
[installed-skill sync update](https://github.com/nebius-academy-templates/AI-for-Kotlin-practice/pull/5).
Older versions only synchronize the two original starter skills.

The package contains canonical skills. After copying them, generate their
Claude Code mirrors from the practice repository root with the project's
skill sync script:

```shell
python scripts/sync_agent_skills.py
python scripts/sync_agent_skills.py --check
```

Use `python3` on macOS/Linux if that is your Python command. The current sync
script discovers installed skills, including both generation skills, and
writes `.claude/skills/<skill-name>/SKILL.md`. Keep `.agents/skills/` as the
source; generate mirrors rather than editing them. This package does not
require additional agent metadata files.

## Assets

| Path | Purpose |
|---|---|
| `.agents/skills/gen-mobile-test/SKILL.md` | Create or validate the mobile plan, then generate one Kotlin/JUnit 5 Appium test case |
| `.agents/skills/gen-api-test/SKILL.md` | Create or validate the API plan, then generate one Kotlin/JUnit 5 REST Assured test case |
| `automation_plan.mobile.md.template` | Draft the implementation plan for a mobile test case |
| `automation_plan.api.md.template` | Draft the implementation plan for an API test case |

## Use a template

Supply the complete test case to the matching skill and request a plan. The
skill checks existing coverage first. When it confirms a gap, it creates or
validates `automation_plan.md` using the layer's template and current project
sources. If the file describes the previous lesson's case, explicitly request
replacement. A planning-only request stops before test-code changes and test
execution.

For **MOB-1006 in lesson 2.3**, review the completed mobile plan and paste it
into the LMS AI checker. Fix any blocking issue and obtain `PASSED` before
using the plan to generate the test in lesson 2.4. The skill's source checks
do not replace this result, and the skill must not write its own checker
verdict. Keep the mobile template's external-validation status fields.

For **API-2004 in lesson 2.5**, `gen-api-test` performs the automated plan
validation. Its lesson dry run may create or correct `automation_plan.md`,
then stops without changing test code or running tests. No separate LMS plan
checker or plan approval is required. Invoke the skill productively with the
validated plan, preserve its allowed-file scope, and verify API-2004 in the
complete fresh API suite.

Keep one active `automation_plan.md` for the test case being implemented.
