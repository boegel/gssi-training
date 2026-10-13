# Exercise: Compiling software with Go

In this exercise, you will compile `hey`, a small command-line application written in Go, using the built-in `go` tool.

Load an available Go module:

```bash
module load Go/1.25.3
```

You need the source code, which in this case is available through GitHub. Clone the repository and enter the source directory:

```bash
git clone https://github.com/rakyll/hey.git
cd hey
```

Select a version, for example `v0.1.5`:

```bash
git switch --detach v0.1.5
```

Inspect the source directory:

```bash
ls
```

Which files indicate that this is a Go project?

If needed, you can update the module dependencies with:

```bash
go mod tidy
```
`go mod tidy` updates the module dependencies and may create or update the `go.sum` file, which records checksums for downloaded modules.

Build the software and place the executable in a `bin` directory:

```bash
mkdir -p bin
go build -o ./bin/hey ./
```

You can use `go help build` to inspect more build options.

Optionally, add this directory to your `PATH`:

```bash
export PATH=$PWD/bin:$PATH
```

Test the resulting executable:

```bash
hey -n 100 https://example.com
```

Note: Go builds for a baseline CPU architecture by default, providing good portability across CPUs. ISA-level optimization can be enabled, for example on x86-64 with:

```bash
GOAMD64=v3 go build -o ./bin/hey ./
```

This can improve performance, but the resulting executable may not run on CPUs that do not support the required instruction set.
