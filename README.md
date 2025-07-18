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

initialise the opam switch
```bash
eval $(opam env)
```

The repository already contains a build. You can directly run command #3. If that does not work: 

Cleans the previous build (if needed)
```bash
dune clean
```

Builds the executable (if needed)
```bash
dune build
```
After running the above command, you will get the output: 
```bash
ld: warning: -undefined suppress is deprecated
ld: warning: -undefined suppress is deprecated
File "test/explicit_typing.ml", line 13, characters 0-23:
13 | let f (x : int) = x * 2;;
     ^^^^^^^^^^^^^^^^^^^^^^^
Error: Functions must have type annotations on all parameters and on the return type.
File "test/test_ppx_1.ml", lines 3-5, characters 2-6:
3 | ..for i = 0 to 10 do
4 |     Printf.printf "i = %d\n" i
5 |   done
Error: For-loops are not permitted (-allow_for_loops is false).
```
The warnings can be ignored. The remaining 2 errors are actually results of the proprocessor on the test files (it accurately bans untyped functions and for-loops). You can play around with the test files by uncommenting certain tests. You can also add more .ml files to test. But after adding them, also configure test/dune accordingly:
```bash
(tests
 (names test_ppx_1 explicit_typing /add more names here/ )
 (preprocess
  (pps ppx_1)))
```

Run the executable on any file
```bash
dune exec ./bin/checker.exe -- /path/to/your/file
```

Here is what a success message looks like 
```bash
✅ YAYCaml! path/to/your/file
```

Here is what an error message looks like
```bash
🐫 OOPSCaml! Error: path/to/your/file
```

Here is a list of flags you can use. Flags must come after the file name with the - as shown below.
```bash
-allow_for_loops -allow_while_loops -allow_mutability -allow_lambdas
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
