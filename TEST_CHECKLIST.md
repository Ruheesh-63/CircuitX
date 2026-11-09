# CircuitX Premium Spark Free · UI smoke checks

1. Open on Live Server at `http://localhost:5500/index.html`.
2. iPhone-style liquid glass header, hero, project cards, gallery, footer render.
3. Toggle Tamil / English; toggle Dark / Light.
4. Search `greenhouse`, click Smart Farming and All category buttons.
5. Reduce browser width to phone view, open/close mobile menu.
6. Click Login → Continue with Google. Must have correct Firebase web config, Google provider and Authorized Domains.
7. Create/verify test user; download asks for login when anonymous and requires verification.
8. Sign in using approved Admin Gmail + active UID document. Dashboard visible.
9. Upload a short `.ino` file; verify `projects` and `projectCodeFiles` documents exist, no Storage bucket used.
10. Test code download as verified user; no `codeText` in public projects documents.
11. Submit Contact Form from verified user; check Admin Inbox.
12. Delete project; both metadata and source code docs removed.
13. All authorization checks require deployed Firestore Rules; use `SECURITY_TESTS.md`.
