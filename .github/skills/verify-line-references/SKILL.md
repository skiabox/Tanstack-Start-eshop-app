---
name: verify-line-references
description: "Use when citing file paths with line numbers, updating markdown docs with code references, explaining code with exact line links, or after files have been edited and line numbers may have shifted. Verify current line numbers before citing them, and prefer file-only references if exact lines have not been re-checked."
---

# Verify Line References

Use this skill whenever you are about to mention exact file line numbers in explanations, reviews, markdown docs, or architecture notes.

## Goal

Prevent stale or incorrect line references after files have changed.

## When To Use

- You are citing exact lines in a response.
- You are writing or updating markdown documentation that contains file links with `#L` anchors.
- You recently edited a file and want to mention a specific line afterward.
- The user called out incorrect line references.
- You are not fully confident that previously observed line numbers are still current.

## Rules

1. Treat line numbers as unstable after any edit.
2. Re-check the current file state before citing exact lines.
3. Do not reuse old line numbers from memory, prior tool output, or pre-edit notes.
4. If exact line verification has not been done, use a file-only reference instead of a line-specific reference.
5. When a document inside the repo contains line-specific links, re-validate those links if the referenced files have changed.

## Recommended Workflow

1. Identify every file you plan to cite.
2. Re-read the relevant file or run a targeted search for the exact symbol or text you want to reference.
3. Capture the fresh line number from current tool output.
4. Use that fresh line number immediately in the response or documentation update.
5. If additional edits happen afterward, repeat the verification step before citing lines again.

## Practical Heuristics

- Prefer `grep_search` for locating exact symbols or phrases quickly.
- Prefer `read_file` when you need surrounding context before citing a line.
- If a section is still moving during edits, cite the file without a line number until the content stabilizes.
- When updating a markdown explainer, verify the top few referenced anchors first, not just the prose.

## Examples

Good:

- Re-run a search for `export const mutateCartFn = createServerFn` and cite the fresh line.
- Re-open the current version of a file after applying a patch, then reference the verified line.

Bad:

- Reusing a line number from a response written before the file changed.
- Quoting line anchors from a markdown document without checking whether the source file moved.

## Fallback

If exact lines cannot be verified quickly, say what is true without over-claiming precision:

- cite the file only
- reference the symbol name
- explain that the file changed and exact line numbers were not re-verified yet
