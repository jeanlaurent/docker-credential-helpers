## Introduction

docker-credential-helpers is a suite of programs to use native stores to keep Docker credentials safe.

## Installation

Go to the [Releases](releases) page and download the binary that works better for you. Put that binary in your `$PATH`, so Docker can find it.

### Building from scratch

The programs in this repository are written with the Go programming language. These instructions assume that you have previous knowledge about the language and you have it installed in your machine.

1 - Download the source and put it in your `$GOPATH` with `go get`.

```
$ go get github.com/calavera/docker-credential-helpers
```

2 - Use `make` to build the program you want. That will leave any executable in the `bin` directory inside the repository.

```
$ cd $GOPATH/calavera/docker-credentials-helpers
$ make osxkeychain
```

3 - Put that binary in your `$PATH`, so Docker can find it.

## Usage

Set the `credsStore` option in your `.docker/config.json` file with the suffix of the program you want to use. For instance, set it to `osxkeychain` if you want to use `docker-credential-osxkeychain`.

```json
{
  "credsStore": "osxkeychain"
}
```

### Available programs

1. osxkeychain: Provides a helper to use the OS X keychain as credentials store.

## Development

Adding a new helper program is pretty easy. You can see how the OS X keychain helper works in the [osxkeychain](osxkeychain) directory.

1. Implement the interface `credentials.Helper` in `YOUR_PACKAGE/YOUR_PACKAGE_$GOOS.go`
2. Create a main program in `YOUR_PACKAGE/cmd/main_$GOOS.go`.
3. Add make tasks to build your program and run tests.

## License

MIT. See [LICENSE](LICENSE) for more information.
