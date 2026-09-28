# Srivatsan Samraj

Information security graduate student at Carnegie Mellon University, graduating December 2026.
I currently work on formal verification of Rust. I'm interested in systems, security, and building
and securing AI agents.

## Kani and the Rust standard library

My master's practicum at Carnegie Mellon, sponsored by Amazon Web Services, is on the effort to
[verify the Rust standard library](https://github.com/model-checking/verify-rust-std). For it, since
September 2026 I have contributed to [Kani](https://github.com/model-checking/kani), an open-source
model checker for Rust. Most of the work is in autoharness, the Kani feature that generates a
verification harness for every function in a crate.

Merged:

- [#4804](https://github.com/model-checking/kani/pull/4804),
  [#4806](https://github.com/model-checking/kani/pull/4806),
  [#4824](https://github.com/model-checking/kani/pull/4824): generate `&CStr`, `&ByteStr` and
  `&Formatter` arguments, so autoharness covers the functions that take them.
- [#4802](https://github.com/model-checking/kani/pull/4802): verify every formatting trait
  implementation.
- [#4793](https://github.com/model-checking/kani/pull/4793): configurable bounds for generated
  arguments, reported in the run summary.
- [#4801](https://github.com/model-checking/kani/pull/4801): code generation for `Box` walks the
  pattern type inside `NonNull`.
- [#4799](https://github.com/model-checking/kani/pull/4799): optional hooks are treated as optional
  in the missing-function check.
- [verify-rust-std #680](https://github.com/model-checking/verify-rust-std/pull/680): the
  autoharness analyzer reads current Kani skip reasons.

[#4822](https://github.com/model-checking/kani/issues/4822) measured false regression alarms in
Kani's benchmark CI; a maintainer opened [#4846](https://github.com/model-checking/kani/pull/4846)
to fix them.

Looking for full-time roles from January 2027:
[LinkedIn](https://www.linkedin.com/in/srivatsan-samraj/).
