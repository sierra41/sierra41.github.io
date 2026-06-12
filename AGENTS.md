# AGENTS.md

## Project Direction

This repository is Sierra's personal blog, built with Jekyll and the Minimal Mistakes theme.

The blog should gradually move away from older study-log style posts and become a place for:

- Development logs for apps Sierra is building.
- Basic information pages for those apps.
- Privacy policy pages and other app-related public documents.
- A cleaner category structure focused on apps, development notes, releases, and policies.

Older posts may be hidden or archived, but do not delete them unless Sierra explicitly asks.

## Collaboration Rules

Do not immediately change, execute, or deploy when Sierra describes an idea.

Default workflow:

1. Understand the request and inspect the relevant files.
2. Explain the proposed design, file changes, and implementation approach.
3. Show the full code or the exact patch plan when the change is meaningful.
4. Wait for Sierra to explicitly say to execute, implement, apply, or deploy.

Only run implementation, destructive, publishing, or deployment steps after explicit approval.

Examples of explicit approval:

- "실행해"
- "적용해"
- "수정해"
- "구현해"
- "배포해"
- "그대로 진행해"

If Sierra asks only for a plan, design, review, category proposal, draft text, or migration strategy, provide that without editing files.

## Deployment Rules

Never deploy automatically.

Before deployment:

- Explain what will be deployed.
- Confirm the target branch and hosting target.
- Run the appropriate local checks when possible.
- Wait for Sierra's explicit deployment instruction.

## Content Handling

When changing posts or pages:

- Preserve existing content unless the request clearly asks to rewrite, hide, archive, or remove it.
- Prefer hiding or excluding old posts over deleting files.
- Keep front matter valid for Jekyll.
- Use clear categories and tags that match the new blog direction.
- For privacy policies, keep wording plain, accurate, and app-specific.

## Code Style

- Follow the existing Jekyll and Minimal Mistakes structure.
- Keep changes small and easy to review.
- Avoid unrelated refactors.
- Prefer Korean for blog-facing content unless Sierra asks otherwise.
- Use English for config keys, filenames, and conventional technical identifiers.

## Verification

When implementation is approved:

- Check the changed files.
- Run a local build or the closest available validation command when practical.
- Report what changed and what was verified.
