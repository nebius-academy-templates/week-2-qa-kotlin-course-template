# Week 2 Kotlin QA course assets

Install this package in the student repository before Module 2 test-generation
exercises. Copy the package contents into the student repository root, in the
same directory as `AGENTS.md`.

## Required layout

```text
student-repository/
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

Do not create tool-specific skill mirrors or metadata files from this package.

## Assets

| Path | Purpose |
|---|---|
| `.agents/skills/gen-mobile-test/SKILL.md` | Generate one approved Kotlin/JUnit 5 Appium Test Case |
| `.agents/skills/gen-api-test/SKILL.md` | Generate one approved Kotlin/JUnit 5 REST Assured Test Case |
| `automation_plan.mobile.md.template` | Draft the implementation plan for a mobile Test Case |
| `automation_plan.api.md.template` | Draft the implementation plan for an API Test Case |

## Use a template

1. Select the template for the Test Case layer.
2. Copy it to `automation_plan.md` in the student repository root.
3. Replace every placeholder and remove unused rows.
4. Review and approve the plan before test generation.
5. Invoke the matching generation skill from the student repository root.

Keep one active `automation_plan.md` for the Test Case being implemented.
