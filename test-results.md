# Alas PR #2506 desktop verification

Tested commit: `71c5950372a716934b769de980806beae2a0e53d`  
Environment: macOS 27.2.1 (26B131), arm64, Xcode 27.2 (27B52).

## Desktop

Opened the Debug build in a separate Alas profile with an empty Git repository. Started native Claude Code 2.1.310 through its installed `claude` symlink in one terminal pane and npm Codex 0.164.0 through its installed `codex` launcher in a second pane.

The Agent sidebar showed both agents as Running at the same time. Its accessibility descriptions were “Codex, Running” and “Claude Code, Running”. This check covers process detection and the Running badge.

## Automated tests

- Focused Xcode app test suite: 13 tests passed, including both parameterized cases of `detectsManuallyLaunchedAgentInPersistentTerminal`.
- Full AlasCore suite: 1,346 tests in 140 suites passed, including the versioned Claude binary and npm Codex launcher regressions.
- The Claude and Codex recognition cases each failed before their respective detector changes.

The local Xcode 27 build used `CARGO_PROFILE_RELEASE_STRIP=none` for Rust helper builds due to rust-lang/rust#157750.
