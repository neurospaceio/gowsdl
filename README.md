# WSDL to Go

Generates Go code from a WSDL file.

## Fork

This is a fork of [hooklift gowsdl](https://github.com/hooklift/gowsdl) which we have modified such that we can use it with WCF 4.5 services.
Modifications

* Use s: instead of soap: as this seem to be the standard in WCF 4.5
* Fix serialization / autoproperties errors which incorrectly gives us fields names starting with `_` which is not a public field in go (MSBingo func)
* Fix import part to be https://github.com/neurospaceio/gowsdl

### Install

* Download and build locally: `go get github.com/neurospaceio/gowsdl/...`

### Goals
* Generate idiomatic Go code as much as possible
* Support only Document/Literal wrapped services, which are [WS-I](http://ws-i.org/) compliant
* Support:
	* WSDL 1.1
	* XML Schema 1.0
	* SOAP 1.1
* Resolve external XML Schemas
* Support external and local WSDL

### Caveats
* Please keep in mind that the generated code is just a reflection of what the WSDL is like. If your WSDL has duplicated type definitions, your Go code is going to have the same and may not compile.

### Usage
```
Usage: gowsdl [options] myservice.wsdl
  -o string
        File where the generated code will be saved (default "myservice.go")
  -p string
        Package under which code will be generated (default "myservice")
  -i    Skips TLS Verification
  -v    Shows gowsdl version
  ```
