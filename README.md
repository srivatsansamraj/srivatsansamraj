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

Merged, 13 in Kani and 3 in verify-rust-std as of 5 October 2026:

- [#4804](https://github.com/model-checking/kani/pull/4804),
  [#4806](https://github.com/model-checking/kani/pull/4806),
  [#4809](https://github.com/model-checking/kani/pull/4809),
  [#4824](https://github.com/model-checking/kani/pull/4824): generate `&CStr`, `&ByteStr`,
  `&Wtf8` and `&Formatter` arguments, so autoharness covers the functions that take them.
- [#4862](https://github.com/model-checking/kani/pull/4862): generated `&Wtf8` values include unpaired
  surrogates, which Windows file names can contain and valid UTF-8 cannot.
- [#4802](https://github.com/model-checking/kani/pull/4802): verify every formatting trait
  implementation.
- [#4793](https://github.com/model-checking/kani/pull/4793): configurable bounds for generated
  arguments, reported in the run summary.
- [#4864](https://github.com/model-checking/kani/pull/4864): autoharness no longer generates arguments that
  hold a `NonNull`. verify-rust-std builds those pointers from arbitrary integers, so the
  harnesses were checking pointers to nothing.
- [#4801](https://github.com/model-checking/kani/pull/4801): code generation for `Box` walks the
  pattern type inside `NonNull`.
- [#4892](https://github.com/model-checking/kani/pull/4892): a pointer to a function item, or a `Box` of
  one, keeps the value assigned to it. Kani used to replace it with a fixed expression, which
  crashed the compiler or read a null pointer as non-null.
- [#4861](https://github.com/model-checking/kani/pull/4861): removed `deref_box`, code that could never run.
- [#4922](https://github.com/model-checking/kani/pull/4922): a SIMD intrinsic called on a non-vector type
  is reported as unsupported instead of crashing the compiler. The crash stopped `core` from
  compiling under autoharness.
- [#4799](https://github.com/model-checking/kani/pull/4799): optional hooks are treated as optional
  in the missing-function check.
- [verify-rust-std #680](https://github.com/model-checking/verify-rust-std/pull/680): the
  autoharness analyzer reads current Kani skip reasons.
- [verify-rust-std #704](https://github.com/model-checking/verify-rust-std/pull/704): the `decimal_seq`
  proofs pass again on the August library update. `u64::pow` now goes through a loop whose Kani
  invariant keeps only "the result is positive", so the annotations use a table of powers of ten.
- [verify-rust-std #705](https://github.com/model-checking/verify-rust-std/pull/705): the ESBMC and
  autoharness-analyzer scripts find Kani's outputs under cargo's per-package build layout.

In review:

- [#4934](https://github.com/model-checking/kani/pull/4934): `simd_reduce_max` and `simd_reduce_min` on integer lanes. The ARM version
  of `is_ascii` in the current library uses them.
- [#4972](https://github.com/model-checking/kani/pull/4972): a SIMD splat, extract, insert or shuffle instantiated with the wrong types
  is reported as unsupported. It used to stop the whole crate from compiling.
- [#4973](https://github.com/model-checking/kani/pull/4973), [#4974](https://github.com/model-checking/kani/pull/4974),
  [#4975](https://github.com/model-checking/kani/pull/4975): three compiler crashes on code optimized with `-Zmir-opt-level=2`: after a
  subslice, on an always-out-of-bounds constant index, and on an invalid `bool` constant, which is now
  reported as undefined behavior.

Reported:

- [#4971](https://github.com/model-checking/kani/issues/4971): Kani proved false assertions about constant slices that start inside
  another constant, because it read them as the whole constant.
- [#4822](https://github.com/model-checking/kani/issues/4822): Kani's benchmark CI failed PRs for
  solver-time regressions that were only noise. I measured the noise and proposed two changes to
  the check. [#4846](https://github.com/model-checking/kani/pull/4846) built on both.


Looking for full-time roles from January 2027:
[LinkedIn](https://www.linkedin.com/in/srivatsan-samraj/).
