# CircuitX Free Edition · test matrix

| Test | Expected result |
|---|---|
| Anyone opens site | Project titles/cards/gallery visible; no code text in HTML or public project documents |
| Anonymous attempts `get(projectCodeFiles/id)` | **PERMISSION_DENIED** from Firestore |
| Anonymous attempts `list(projectCodeFiles)` | **PERMISSION_DENIED** |
| Logged-in but UNVERIFIED email attempts `get` | **PERMISSION_DENIED** |
| Logged-in + verified email attempts `get` of published code file | Allowed; source text downloads |
| Normal verified user attempts create project | **PERMISSION_DENIED** |
| Admin email but missing `admins/<UID>` active flag attempts upload | **PERMISSION_DENIED** |
| Admin verified and UID flagged active publishes project with `.ino` | Atomic write of `projects/id` + `projectCodeFiles/id` succeeds |
| Admin publishes project without code | `projects/id` only and no download button |
| Admin tries upload `.zip` or >80 KiB | Client rejects with explanation |
| Admin deletes project and code file | Both Firestore docs removed in a batch |
| Verified user submits contact message | Saved in private `messages` collection |
| Normal user attempts read admin inbox | **PERMISSION_DENIED** |
| Refresh site on mobile | Gallery, filters, theme and language still render |

## Important

- Publishing these Rules to Firestore is required before the tests.
- Verify admin UID document exists in `admins` with boolean `active: true`.
- Firebase emulator / actual Firebase project required for real permission tests; local browser preview alone cannot prove remote rule behavior.
- Existing Storage-based source files are not migrated automatically; re-upload small UTF-8 text source in Dashboard.
