## Guardrails

- Publish only generic fixture evidence. Keep private application captures, logs and integration backups outside the repository and release artifacts: public disclosure cannot be undone by adding gitignore rules later.
- Reserve the Windows desktop before native-input tests and target only owned fixture processes. Native input can affect another application if foreground ownership changes.
- Require explicit approval before registry publication. Versions are immutable and publication across npm and crates.io is not atomic; inspect partial results before resuming.

## Testing decisions

- Put TypeScript unit tests beside the implementation and Rust unit tests in the module they cover. Behavior changes require a regression test at the nearest meaningful layer.
- Verify named pipes, WebView2 and Windows input through the live fixture. A dispatch acknowledgement or safe native rejection is not proof of an observed effect.
- Exclude generated bundles, permission schemas and third-party internals from direct unit tests. Validate their integration through packaging and consumer tests.
- Existing tests may be corrected, but assertions must not be weakened to make CI pass.
