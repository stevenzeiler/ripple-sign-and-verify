# Status

Last reviewed: 2026-11-20 (github-audit pass 02, documentation only; no code was run).

## What works

- Nothing has been verified in this pass.
- `Message` validates that it gets a non-empty string.
- Every class has a spec, written first (the one commit is `[TEST] Fully spec signing and verifying library`).

## What's broken or unknown

- Signing is not implemented: `Signature` throws "Signature generation not implemented".
- `PrivateKey` and `PublicKey` are empty classes, so no key is parsed or checked.
- `Verifier.verify` validates its arguments and returns nothing.
- `Signer.sign` calls `assert` without defining it (the other classes use `utils.assert`). **(inference from reading the code)**
- The source requires a module named `utils` that is not in `package.json`, and `package.json` has no `gulp`, `gulp-6to5` or `mocha`.
- The committed `npm-debug.log` records a failed `npm run build` on Node 0.10.32 and npm 1.4.28.
- `.gitignore` does not ignore `build/` or `npm-debug.log`.
- Secret-looking strings: the original README (before this PR) and the files `test/signer.js`, `test/verifier.js` and `test/private_key.js` hold strings in Ripple secret-key format (`test/public_key.js` holds only a public address). They are probably throwaway sample keys, which is unverified. This PR replaces the README ones with placeholders, but the tests and git history still hold them. Rotation or history cleanup, if wanted, is Steven's call.

## What's next

Nothing planned. If revived: pick a real signing library, implement the key classes and `Signature`, add the missing dependencies, and replace test keys with generated ones.

## Not yet from the standard

- CONTRIBUTING.md
- SECURITY.md
- `.editorconfig`
- `.github` issue and PR templates
- Dependabot
- `ci.yml` with gitleaks
- master to main rename
- CloudEvents catalog
- Product one-pager
