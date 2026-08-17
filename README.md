<p align="center">
  <img src="./assets/hero.svg" width="100%" alt="LeiZ — systems and machine-learning engineering" />
</p>

<p align="center">
  <b>CS Student · Systems Builder · ML Engineer</b><br />
  <sub>From kernel primitives to neural networks — built to understand how the layers actually work.</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/C-systems-0B1220?style=flat-square&logo=c&logoColor=41D1FF" alt="C systems" />
  <img src="https://img.shields.io/badge/Go-runtimes-0B1220?style=flat-square&logo=go&logoColor=41D1FF" alt="Go runtimes" />
  <img src="https://img.shields.io/badge/Rust-browsers-0B1220?style=flat-square&logo=rust&logoColor=C35BFF" alt="Rust browsers" />
  <img src="https://img.shields.io/badge/Python-ML-0B1220?style=flat-square&logo=python&logoColor=C35BFF" alt="Python machine learning" />
</p>

I build compact, inspectable implementations of the layers developers usually consume as abstractions. The common thread is turning an idea into code with explicit invariants, automated tests, reproducible commands, and honest scope boundaries.

---

## `01 / flagship systems`

<table>
<tr>
<td width="50%" valign="top">
<h3>01 · <a href="https://github.com/Lei-TzuY/minios-x86">miniOS</a></h3>
<p><code>C</code> <code>x86</code> <code>Kernel</code></p>
<p>Bootable 32-bit OS with Ring-3 userspace, preemptive scheduling, COW <code>fork</code>, demand paging, VFS, filesystems, signals, and IPC.</p>
<p><b>Inspect:</b> <a href="https://github.com/Lei-TzuY/minios-x86/tree/main/tests">native + QEMU tests</a> · <a href="https://github.com/Lei-TzuY/minios-x86/actions/workflows/tests.yml">CI</a> · <a href="https://github.com/Lei-TzuY/minios-x86/blob/main/tests/BENCHMARKS.md">benchmarks</a></p>
</td>
<td width="50%" valign="top">
<h3>02 · <a href="https://github.com/Lei-TzuY/mini-container-runtime">Mini Container Runtime</a></h3>
<p><code>Go</code> <code>Linux</code> <code>OCI</code></p>
<p>Namespaces, cgroups v2, <code>pivot_root</code>, OverlayFS, veth networking, OCI image pulling, capabilities, and seccomp.</p>
<p><b>Inspect:</b> <a href="https://github.com/Lei-TzuY/mini-container-runtime/tree/main/internal">package tests</a> · <a href="https://github.com/Lei-TzuY/mini-container-runtime/actions/workflows/tests.yml">CI</a> · <a href="https://github.com/Lei-TzuY/mini-container-runtime#scope-and-limitations">limits</a></p>
</td>
</tr>
<tr>
<td width="50%" valign="top">
<h3>03 · <a href="https://github.com/Lei-TzuY/userspace-tcpip-stack">Userspace TCP/IP Stack</a></h3>
<p><code>C99</code> <code>Networking</code> <code>PCAP</code></p>
<p>Packet parsing, PCAP/PCAPNG, reassembly, TCP state and stream analysis, protocol decoders, and recursive tunnels.</p>
<p><b>Inspect:</b> <a href="https://github.com/Lei-TzuY/userspace-tcpip-stack/tree/main/tests">fixtures + tests</a> · <a href="https://github.com/Lei-TzuY/userspace-tcpip-stack/actions/workflows/ci.yml">sanitizer/fuzz CI</a> · <a href="https://github.com/Lei-TzuY/userspace-tcpip-stack/tree/main/fuzz">fuzz corpus</a></p>
</td>
<td width="50%" valign="top">
<h3>04 · <a href="https://github.com/Lei-TzuY/toy-browser-engine">Toy Browser Engine</a></h3>
<p><code>Rust</code> <code>Layout</code> <code>DOM</code></p>
<p>HTML/CSS parsing, cascade, layout, painting, DOM events, scripting, fetch, timers, and microtasks.</p>
<p><b>Inspect:</b> <a href="https://github.com/Lei-TzuY/toy-browser-engine/tree/main/tests">integration tests</a> · <a href="https://github.com/Lei-TzuY/toy-browser-engine/actions/workflows/tests.yml">CI</a> · <a href="https://github.com/Lei-TzuY/toy-browser-engine#architecture">architecture</a></p>
</td>
</tr>
<tr>
<td width="50%" valign="top">
<h3>05 · <a href="https://github.com/Lei-TzuY/pygit-sha256">pygit</a></h3>
<p><code>Python</code> <code>Version Control</code> <code>SHA-256</code></p>
<p>Content-addressed objects, refs, index/worktree operations, history, packs, and selected remote workflows in an inspectable repository format.</p>
<p><b>Inspect:</b> <a href="https://github.com/Lei-TzuY/pygit-sha256/tree/main/tests">test suite</a> · <a href="https://github.com/Lei-TzuY/pygit-sha256/actions/workflows/tests.yml">multi-version CI</a> · <a href="https://github.com/Lei-TzuY/pygit-sha256/blob/main/INTERNALS.md">internals</a></p>
</td>
<td width="50%" valign="top">
<h3>06 · <a href="https://github.com/Lei-TzuY/tiny-transformer-autograd">Tiny Transformer + Autograd</a></h3>
<p><code>NumPy</code> <code>Autograd</code> <code>Transformer</code></p>
<p>Reverse-mode autodiff, GPT/Llama-style components, training, KV caching, checkpointing, and numerical validation.</p>
<p><b>Inspect:</b> <a href="https://github.com/Lei-TzuY/tiny-transformer-autograd/tree/main/tests">numerical tests</a> · <a href="https://github.com/Lei-TzuY/tiny-transformer-autograd/actions/workflows/tests.yml">multi-version CI</a> · <a href="https://github.com/Lei-TzuY/tiny-transformer-autograd/blob/main/src/benchmark.py">benchmark entrypoint</a></p>
</td>
</tr>
</table>

---

## `02 / engineering method`

```text
$ ./build --from-first-principles
specify invariant → build complete path → test failure modes → measure → document limits
```

- **Correctness over adjectives:** important claims point to tests, workflows, benchmarks, or reproducible commands.
- **End-to-end where integration matters:** QEMU boots, generated packet fixtures, real socket tests, and installed-package smoke tests complement unit coverage.
- **Adversarial validation:** sanitizers, fuzzing, mutation checks, numerical gradient checks, and malformed-input corpora are used where appropriate.
- **Scope stated plainly:** these projects expose mechanisms; they do not claim production equivalence to Linux, Docker, Chrome, Git, or mature ML frameworks.

---

## `03 / research + applied systems`

**[TinyDB](https://github.com/Lei-TzuY/tinydb-c)** — compact SQL database in C with B+ tree storage, WAL recovery, transactions, secondary indexes, query execution, and cross-platform CI.

**[Intelligent Software Quality Assurance](https://github.com/Lei-TzuY/Quality_Assurance)** — executable research prototype connecting machine-readable quality rules, runtime observations, traceability, and quantitative NFR scoring.

**[Candy Defect Detection](https://github.com/Lei-TzuY/candy_detect)** — multi-camera computer-vision workflow for capture, inference, recording, annotation, and reporting. Reproducible evaluation remains the next milestone.

**[Picture Magician](https://github.com/Lei-TzuY/change-clothes)** — Flask + ComfyUI virtual try-on and image-workflow prototype.

---

## `04 / current direction`

I am most interested in **operating systems, runtimes, networking, storage, compilers, software quality, and ML infrastructure** — especially work where correctness is observable and the layer below the abstraction is the interesting part.

<p align="center">
  <sub><code>LeiZ // build · break · measure · harden · repeat</code></sub>
</p>
