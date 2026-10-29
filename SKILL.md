---
name: design-walkthrough
description: Audit and redesign a project's UI with an editable page-by-page review spreadsheet, then implement and compare approved designs when requested. Use for multi-page design reviews, walkthroughs, and review-to-build workflows; not for an isolated UI fix that does not call for a review inventory.
---

# Design walkthrough

Help the user understand what each screen does, review proposed changes, and, when requested, carry the decisions through implementation and verification. Follow the user's requested scope and stop at the requested stage; a request to audit or design does not by itself authorize implementation, publication, or sending anything to others.

When explicitly invoked without an accompanying task, use the current project's screens as the scope: audit them, create an editable Excel review with findings and screenshots, and propose designs consistent with the project's style for the user's review. Start implementation only if the user requests it. Follow any more specific instructions the user supplies.

## Learn the project first

Find the project's instructions, design system, tokens, component demos, brand guidance, narrative, copy and visual assets. Examine the actual application and the reference screens the user identifies. Record the sources that informed the review. If guidance is absent, infer a provisional visual language from existing screens and tell the user what evidence was used; do not invent a project standard or force a generic style. Keep accessibility and usability in view while respecting the product's established character.

## Use project lint as review evidence

Discover the project's stack, workspace boundaries, lint configuration, documented commands, and CI checks. Use its installed tools and package manager; do not assume ESLint, JavaScript, a particular design system, or a command named `lint`. Identify which checks actually cover the reviewed source and design constraints. General code lint passing does not imply design-rule coverage.

Run relevant existing checks in non-fixing mode before the walkthrough when source and tooling are available. Inspect command wrappers for auto-fixes or other mutations, and respect the project's validation scope and lifecycle. Record the command, working directory, checked scope, exit result, and relevant diagnostics. Distinguish violations from unavailable tools, execution failures, excluded files, and unsupported rules. If no suitable checker exists, record the coverage gap and continue the visual review; do not silently install tooling or change configuration during an audit. For screenshot-only or inaccessible-source reviews, mark static checks unavailable.

Relate confirmed diagnostics to the reviewed screens through their actual components and entry points. Keep rule ID, source location, and supporting project guidance with each relevant finding. Group a shared-component cause once and link affected screens; leave uncertain mappings explicitly unresolved. Keep unrelated code diagnostics separate from design findings. Use machine-readable output when supported, preserving existing workbook decisions and annotations when refreshing results.

When adding automated checks is within the user's requested implementation scope, reuse or extend the project's checker for explicit, stable contracts. Define each rule's owner, applicable files, platforms, exceptions, and authoritative source. Examples include token usage, approved component or icon imports, and required accessible-name properties where statically decidable. Do not turn inferred style, one page's preference, or all literal numbers into global prohibitions. Keep project-specific rules in the project, not in this skill. Use structural analysis appropriate to the language; text searches provide candidates, not proof of a semantic violation.

Before enabling a rule, check existing rules for duplication or conflict and test a violating example, a valid example, and an exception or overlapping-rule case. Keep experimental checks report-only without changing existing gates; inspect warning thresholds because warnings may still fail CI. Automatically fix only transformations whose intended replacement is unambiguous and within the authorized scope.

Static checks cannot prove rendered contrast, clipping, responsive layout, task usability, or fidelity to an approved design. Verify those through the actual application and matching visual evidence. Keep static, runtime, and visual results distinct; never label an unchecked category as passed.

## Walk through and organize

Use the actual application and browser automation, such as Playwright, when available. Inventory the requested screens and meaningful states, capture current screenshots, and trace each entry point. For each issue, explain the user's task, where the screen is entered, what is wrong, and which project reference supports the finding. Identify incomplete, unreachable, or unimplemented flows as such; distinguish observations from proposals and do not present fixtures as live data.

Create or update an editable Excel workbook when a page-by-page review is requested. Keep a stable row for each screen or distinct issue, with its purpose, entry/trigger, current screenshot or accessible link, problem, proposed design or link, user decision and annotation, implementation status, and test result. Include a ready-for-development column when useful. Highlight unresolved or blocked items, not successful ones. Follow the user's existing workbook and location when supplied; preserve their selections and notes. Use the available spreadsheet workflow to create and verify the file.

## Design and review

Base proposals on the project's visual language, product narrative, characters, components, and user tasks. Respect supplied materials without assuming that every existing element must be reused. Make new assets when the task calls for them, and consider payload and platform constraints. Design page layouts for the requested devices; if requirements specify multiple viewports, create purpose-built layouts for each. Show the current screen and entry context alongside proposals when available. Provide the requested number of options and editable feedback controls when the user asks for an interactive review. Preserve existing decisions and drafts.

Render and inspect designs for hierarchy, contrast, spacing, clipping, consistent controls, asset compositing and text density; revise obvious defects before handing them over. Label proposed states and assumptions clearly. Update the workbook and any user-selected review surface so the decision and its matching design can be found together.

## Implement and verify when requested

Implement the user's selected or otherwise authorized design using the project's own components, tokens, and platform rules. Do not silently redesign the approved target to match the implementation. Exercise the affected flows through real entry points and capture actual implementation screenshots at matching viewport sizes and states. Place each screenshot beside or link it from the matching design and workbook row. Inspect both, fix observable differences, and repeat. Clearly mark unverified states, remaining differences, test data, and platform limitations instead of claiming a match without evidence.

Preserve user work and existing review records. Rerun relevant project checks after implementation and update the associated findings with resolved, remaining, or unverified results. Leave an accessible preview when required, and summarize what is complete and what remains, including automated-check coverage gaps. Commit, push, publish, or send messages only when authorized.
