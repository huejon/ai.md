# Finding — Legacy local directory cleanup

Date: 2026-06-30

## Evidence

- User explicitly authorized deleting `.agents/`, `.claude/`, and `.factory/` entirely.
- User explicitly authorized cleaning `.opencode/` down to the high-signal project files needed for future long-horizon work.
- Pre-cleanup `git ls-files` showed tracked local prompt/skill/droid copies and OpenCode agent copies in those paths.
- Pre-cleanup `.opencode/` also contained package/dependency artifacts that were not required for the retained `/daily-cron` command, policy, config, or ledger.

## Conclusion

The deleted directories were legacy local deployment/copy surfaces or noisy setup artifacts. The retained high-signal surfaces are root policy/docs, harness/docs, canonical `agents/` and `skills/` development artifacts, `knowledge/`, `templates/`, `guides/`, and the minimal OpenCode overlay.

## Rollback

Restore any removed path from git history if future local deployment or package-managed OpenCode extensions are intentionally reintroduced.
