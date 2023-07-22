# go-webassembly

a simple project to learn webassembly with go

## STEPS

1. Create basic vanilla javascript web project
2. Create go project with: `go mod init <project-name>`
3. Compile go main package code into wasm file with: `GOOS=js GOARCH=wasm go build -o ../main.wasm`
   1. If you get the error of `GOOS is not recognized command` try switching to other terminal like git bash.
4. Copy go js connection script with: `cp "$(go env GOROOT)/misc/wasm/wasm-exec.js"`
5. Make sure to import the connection script before your personal scripts in the Html
6. Connect to the WebAssembly file from javascript like this: 
   ```
    const go = new Go();

    WebAssembly.instantiateStreaming(fetch("main.wasm"), go.importObject).then((result) => {
      go.run(result.instance);
    });
   ```