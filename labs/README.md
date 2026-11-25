# Lab Guides

**Status:** No LionraForge implementation labs have been completed or published in this review package.

I will organise labs in chronological phases with descriptive directory names, for example `phase-03-active-directory/01-install-domain-controller/`. These names will be finalised when I begin each lab, not created as empty placeholders now.

## How each lab will be documented

The standard core for a lab guide is:

1. Overview and objectives.
2. Prerequisites and tested environment.
3. Implementation — what, how and why.
4. Verification steps, expected versus actual results, and evidence.
5. Troubleshooting references.
6. Evidence and references.

I'll add sections for design decisions, security, rollback or lessons learned where they help explain real work.

Each lab will keep its own scripts and configurations, a `troubleshooting.md` journal for genuine implementation issues and evidence organised by verification task. Substantial troubleshooting investigations can become linked case studies. Shared scripts may be maintained centrally with an exact version or commit referenced by the lab.

## Verification and honesty

A successful installation alone does not mean a lab is Verified. I'll define acceptance tests, run them, record observed results and link appropriate evidence. Unresolved failures will be documented. Intentional helpdesk scenarios and SOC attack simulations will be labelled as simulations and maintained separately from accidental build problems.

All instructions and images will be reviewed for secrets, tokens, passwords, personal data and details that should not be committed publicly.

[Project roadmap](../docs/roadmap.md)