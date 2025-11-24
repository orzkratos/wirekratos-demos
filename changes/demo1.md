# Changes

Code differences compared to source project demokratos.

## Makefile (+4 -0)

```diff
@@ -25,6 +25,7 @@
 	go install github.com/go-kratos/kratos/cmd/protoc-gen-go-errors/v2@latest
 	go install github.com/google/gnostic/cmd/protoc-gen-openapi@latest
 	go install github.com/google/wire/cmd/wire@latest
+	go install github.com/orzkratos/wirekratos/cmd/wirekratos@latest
 
 .PHONY: config
 # generate internal proto
@@ -62,6 +63,9 @@
 .PHONY: generate
 # generate
 generate:
+	go mod tidy -e
+	go get github.com/google/wire/cmd/wire@latest
+	wirekratos --framework=kratos
 	go generate ./...
 	go mod tidy
 	@# Remove obsolete +build tags from wire_gen.go
```

