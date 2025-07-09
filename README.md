# 🐫 OCaml-PPX

A custom PPX (PreProcessor eXtension) for OCaml.

---

## ⚙️ Setup

### 🔗 Dependencies

Make sure the following dependencies are installed:

- [`dune` ≥ 3.17](https://dune.build/)
- [`ocaml`](https://ocaml.org/)
- [`odoc`](https://ocaml.org/p/odoc) *(with documentation support)*
- [`ppxlib`](https://github.com/ocaml-ppx/ppxlib)

You can install them using [`opam`](https://opam.ocaml.org/):

```bash
opam install dune ocaml odoc ppxlib
```

### ⬆️ Commands

Cleans the previous build
```bash
dune clean
```

Builds the executable
```bash
dune build
```

Run the executable on any file
```bash
dune exec ./bin/checker.exe -- /path/to/your/file
```

### 📂 Project Structure
```bash
ppx_1/
├── bin/
│ ├── checker.ml        # Entry point or CLI tool for testing/running the PPX
│ └── dune        # Build configuration for the executable in bin/
│
├── lib/
│ ├── dune        # Build rules for the main library
│ └── ppx_1.ml        # Core logic of the PPX extension
│
├── test/
│ ├── dune       # Build/test specification for test files
│ ├── explicit_typing.ml        # Test case(s) for the PPX (likely input OCaml code)
│ ├── test_ppx_1.ml        # Main test driver for PPX transformation
│ ├── test_ppx_1.cmi        # Compiled interface file (auto-generated)
│ ├── test_ppx_1.cmo        # Compiled object file (auto-generated)
│ └── test_ppx_1_compiled        # Possibly the output binary or result of PPX compilation
│
├── dune-project        # Project-wide configuration (declares name, version, etc.)
├── ppx_1.opam        # OPAM package file with dependencies and metadata
```
