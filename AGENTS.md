# AGENTS.md

Guidance for AI agents working in this repo. Humans: see [README.md](README.md).

## What this is

`ripple-sign-and-verify` 0.1.0: an ALPHA sketch of signing and verifying messages with Ripple keys. One commit (2014-12-27). The crypto is not implemented. Abandoned.

## Stack

- JavaScript, ES6 classes in `src/`, transpiled to `build/` by gulp 3 and `gulp-6to5`.
- Tests: mocha, run against `build/`.
- `package.json` declares no dependencies. `gulp`, `gulp-6to5` and `mocha` are needed but missing; the source also requires a module named `utils`, which is not declared.
- The committed `npm-debug.log` shows npm 1.4.28 on Node 0.10.32 failing the build script.

## Layout

- `src/` one class per file: message, private_key, public_key, signature, signer, verifier
- `test/` one mocha spec per class
- `gulpfile.js` build
- `npm-debug.log` accidental committed log (leave it unless Steven says delete it)
- `docs/STATUS.md` current state of the repo

## Commands

- Install: `npm install` (installs nothing useful)
- Build: `npm run build` (gulp, needs gulp installed)
- Test: `npm test` (build, then mocha). Known not to work as the repo stands: missing dependencies, and signing throws.

## Rules

- Add or update tests with every change.
- Never commit secrets. The existing README history and tests hold secret-looking strings; use placeholders such as `sXXXXXXXX` and do not copy the old values anywhere.
- Use Conventional Commits.
- Keep `docs/STATUS.md` current.

## Agents may and may not

- May: improve docs, add tests, open PRs on a branch.
- May not: archive the repo, publish to npm, rewrite git history, or implement and ship crypto code, without Steven.
