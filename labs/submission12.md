# Lab 12 submission

## Task 1

**Screenshot of CLI mode output (MODE=once), confirmation that I am working directly in labs/lab12/ directory:**
![12.2]()

**Screenshot of server mode running in browser (if tested)**
![12.1]()

**Explanation of how the single main.go works in three different contexts:**

The program checks environment variables to decide which mode to run in: if `MODE=once` then CLI mode, if `REQUEST_METHOD` is set then WAGI (Spin/WebAssembly) mode, otherwise - standard HTTP server mode.

**CLI / Benchmark Mode (`MODE=once`):**

- Calls `getMoscowTime()`
- Converts the result to formatted JSON
- Prints it to stdout
- Exits immediately

Purpose:
- Quick testing
- Benchmarking
- Running logic without starting a server

**WAGI Mode (Spin / WebAssembly):**

- Handles a single HTTP request
- Reads the request path from `PATH_INFO`
- Writes the response directly to stdout

Routing:
- `/` - returns HTML page
- `/api/time` - returns JSON time
- anything else - returns 404

**Traditional HTTP Server Mode:**

- Starts a standard Go HTTP server on port 8080
- Uses `net/http` package

Routing:
- `/` → serves HTML page
- `/api/time` → returns JSON time

It is long-running process, built-in routing via `http.HandleFunc`.
