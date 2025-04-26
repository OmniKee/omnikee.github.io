+++
title = "Overview"
draft = false
weight = 10
sort_by = "weight"
template = "docs/page.html"

[extra]
lead = 'This page gives a rough architectural overview of the most important aspects of OmniKee.'
toc = true
top = false
+++

# AppState and omnikee-lib

Security-critical state such as the decrypted databases is held in an [`AppState` instance](https://github.com/OmniKee/OmniKee/blob/main/lib/src/lib.rs) that is part of the [`omnikee-lib` crate](https://github.com/OmniKee/OmniKee/tree/main/lib). The crate can be compiled both as a Rust dependency and as a WebAssembly module (see next section).



# Deployment styles

OmniKee can run in a "Tauri" and in a "Web" mode which determines the shape and location of the `AppState` object. In the frontend, the [`omnikee.ts` adapter](https://github.com/OmniKee/OmniKee/blob/main/www/src/omnikee.ts) abstracts away the deployment style behind a common interface used by the rest of the user interface.


## "Tauri" Mode

<img src="../tauri-mode.svg" width="100%" alt="Tauri mode">

<p></p>

When OmniKee is executed as a standalone application, it follows the [recommended architecture of a Tauri application](https://tauri.app/concept/process-model/). `omnikee-lib` is used as a Rust dependency, and the `AppState` is managed as a [Tauri state object](https://tauri.app/develop/state-management/) and its methods are called via Tauri commands.

## "Web" Mode

<img src="../web-mode.svg" width="100%" alt="Web mode">

<p></p>

When OmniKee is running in the browser, `omnikee-lib` is compiled into WebAssembly via [wasm-pack](https://rustwasm.github.io/docs/wasm-pack/) and the methods of the `AppState` are accessed directly from the frontend application.
