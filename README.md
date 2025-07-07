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
├── bin/
│   └── checker.ml        # Main entry point
├── lib/
│   └── my_ppx.ml         # PPX logic
├── test/
│   └── example.ml        # Test files
├── dune-project
└── README.md
```
