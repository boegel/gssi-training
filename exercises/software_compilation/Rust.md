# Exercise: Compiling software with Rust

In this exercise, you will compile `genact`, a small command-line application written in Rust. You will use `cargo`, Rust's package manager and build system.

Load an available Rust module:

```bash
module load Rust/1.91.1-GCCcore-14.2.0
```

You will need the source code. In this case, you can obtain it from GitHub using `git clone`. Clone the repository and enter the source directory:

```bash
git clone https://github.com/svenstaro/genact.git
cd genact
```

Select a version, for example `v1.5.1`:

```bash
git switch --detach v1.5.1
```

Inspect the source directory:

```bash
ls
```

Which files indicate that this is a Rust project using Cargo?

Do you see a `Cargo.lock` file? If not, you can generate one with:

```bash
cargo generate-lockfile
```

The `Cargo.lock` file records the exact versions of the dependencies used by the project. This helps with reproducibility if you or a colleague need to rebuild the software later.

Build the software in release mode:

```bash
cargo build --release
```

You can use `cargo build --help` to inspect the available build options.

Finally, test the resulting executable:

```bash
./target/release/genact --help
```

Note: `cargo build --release` does not specifically optimize for the CPU architecture of the build node. In general, architecture-specific optimization is possible with: 
```bash
RUSTFLAGS="-C target-cpu=native" cargo build --release
```
This may improve performance, but can reduce portability across different CPU types.
