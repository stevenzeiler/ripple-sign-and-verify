# Ripple signature (ALPHA)

Prove identity and ownership of a Ripple secret key using digital signatures. This is the idea; the code is an unfinished first sketch.

> **Status: dormant since 2014, and signing is not implemented.** One commit on 2014-12-27, part of Steven Zeiler's Ripple Labs era. The classes and their tests exist, but `Signature` throws "Signature generation not implemented", `PrivateKey` and `PublicKey` are empty, and `Verifier.verify` checks its arguments and returns nothing. The usage below is the proposed design, not working code. See [docs/STATUS.md](docs/STATUS.md).

## Install

Not published to npm. To look at it:

    git clone https://github.com/stevenzeiler/ripple-sign-and-verify
    cd ripple-sign-and-verify
    npm install

`package.json` lists no dependencies, so `gulp` and `mocha` have to be installed by hand to build and test. Not verified on a current toolchain.

## Proposed usage

    var privateKey = new PrivateKey('sXXXXXXXX');
    var publicKey  = new PublicKey('rXXXXXXXX');

    var message    = new Message('important information to verify');

    var signer     = new Signer(privateKey);
    var signature  = signer.sign(message);

    var verifier   = new Verifier(publicKey);
    assert(verifier.verify(message, signature));

Use placeholders like the ones above in examples. Never put a real Ripple secret in this repo.

## Config

None. No environment variables.

## How it works

Each class lives in its own file in `src/`, with a mocha spec of the same name in `test/`:

- `Message` wraps a non-empty string (the only class with real logic).
- `PrivateKey` and `PublicKey` are empty classes.
- `Signer` takes a private key and `sign(message)` returns a `Signature`.
- `Signature` is meant to sign a message with a private key; it currently throws.
- `Verifier` takes a public key and `verify(message, signature)`.

`src/` is ES6, transpiled to `build/` by gulp and `gulp-6to5`. The tests load from `build/`.

## Status

Abandoned in the sketch stage. It was a direct precursor of the identity-linking idea in Steven's later `attest` repo. See [docs/STATUS.md](docs/STATUS.md).

## License

ISC. See [LICENSE](LICENSE).
