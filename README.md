# config

[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/filipegoncalves/rust-config?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge) [![Build Status](https://travis-ci.org/filipegoncalves/rust-config.svg?branch=master)](https://travis-ci.org/filipegoncalves/rust-config)

# Beta compatibility
Currently this doesn't compile on 1.0.0-beta because `rust-peg` uses features that are not available in the beta channel. I am looking into several options, including switching to [nom](https://github.com/Geal/nom).
In the meantime, just stick to rust nightly and you should be good.

# Goal
A Rust library to read and parse configuration files.

The idea is to make it very similar to [libconfig](http://www.hyperrealm.com/libconfig/), with a few extra additions / tweaks.

This is still under heavy development. As of this writing, the library is still very basic and can only read / load a configuration. It also includes a rudimentary set of methods to browse the loaded data.

# TODO

## Features
- [X] Allow single and multi-line comments in configurations
- [ ] Add `#include` support to include other configuration files
- [X] Automatically concatenate blank-separated string literals in the configuration. Useful for settings with big strings
- [ ] Export a public API to manipulate a configuration in runtime and possibly write it to a file

## Parser
- [X] Figure out why the parser returns an error on a blanks-only configuration
- [ ] Consider splitting the parser into lexer + syntax analyser (much like we would in C with flex + byacc), OR
- [ ] Use [nom](https://github.com/Geal/nom) to generate the parser instead of rust-peg. Rust-peg uses features that will not be available in beta.

## Misc
- [X] Refactor misc types (`Setting`, `SettingsList`, etc) into a separate, independent module
- [X] Write tests that are expected to fail
- [X] Add missing documentation for undocumented code
- [X] Document `parser::ParseErr`
- [X] Write misc documentation with a high level description of the module and its features
- [X] Write integration tests
- [X] Document when, why and how `parse()` returns `Err`
- [ ] `hex` and `hex64` literals support?
- [ ] Add option to indicate the conf. file encoding
- [X] Enforce the rules for arrays. Arrays are homogeneous and can only hold scalar values
