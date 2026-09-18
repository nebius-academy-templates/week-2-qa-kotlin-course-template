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

Don't create tool-specific skill mirrors or metadata files from this package.

## Assets

| Path | Purpose |
|---|---|
| `.agents/skills/gen-mobile-test/SKILL.md` | Generate one validated Kotlin/JUnit 5 Appium test case |
| `.agents/skills/gen-api-test/SKILL.md` | Generate one validated Kotlin/JUnit 5 REST Assured test case |
| `automation_plan.mobile.md.template` | Draft the implementation plan for a mobile test case |
| `automation_plan.api.md.template` | Draft the implementation plan for an API test case |

## Use a template

1. Select the template for the test case layer.
2. Copy it to `automation_plan.md` in the repository root.
3. Replace every placeholder and remove unused rows.
4. Submit the plan to the AI checker and fix every blocking issue.
5. After validation passes, invoke the matching generation skill from the repository root.

Keep one active `automation_plan.md` for the test case being implemented.
