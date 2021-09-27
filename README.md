# GenDocs

## Description

Simple documentation generator for AWK.

## Requirenments

- `GNU Awk 5.0.1`

## Syntax

```sh
awk -f gendocs.awk -- -o|--output <value> -- <input-awk-files>
```

where:

- `-h`|`--help` - prints this help and exits with 0
- `-v`|`--version` - prints version and exits with 0
- `-o`|`--output` - output directory with .md documentation files
- `<input-awk-files>` - set of `.awk` files to parse and generate documentation from.

## Return codes

- `0` - success
- `1` - invalid documentation comment or doc file to be created already exists
- `2` - no files provided

## Error messages

- `1` code:
  - `ERROR[<number> line]: "Description" tag on the first documentation comment line expected.`
  - `ERROR[<number> line]: No trailing empty documentation comment lines expected`
  - `ERROR[<number> line]: "Description" tag is already defined.`
  - `ERROR[<number> line]: "Arguments" tag is already defined.`
  - `ERROR[<number> line]: "Returns" tag is already defined.`
  - `ERROR[<number> line]: "Arguments" tag is unnecessary because no arguments described.`
  - `ERROR[<number> line]: Wrong argument description format.`
  - `ERROR[<number> line]: Wrong return description format.`
- `2` code:
  - `ERROR: no input .awk files to read from provided.`

## Documentation comments

Documentation comments (or simply comments) are single-line comments in .awk programs. They must be placed immidiately before function definition and use the following syntax:

```awk
# Description: function description
#
# Arguments:
# - argument-name: argument-type - argument-description
# ...
#
# Returns: return-type: return-description
#
# Example:
#   example-code
function Some(args) {
}
```

If you don't know which type to specify you can write `any` instead of it. It is also useful when it doesn't matter which type parameters have.

Example:

```md
# Description: Calculates integer sum.
#
# Arguments:
# - a: number - first number
# - b: number - second number
#
# Returns: number: number sum
#
# Example:
#   Sum(1, 2)
function Sum(a, b) {
  return a + b
}
```

## Documentation format

Generated documentation has the following format:

```md
# AWK-file-name-without-extension

## function-name(argument-type)

Description.

Arguments:
- `argument-name`: argument-type - argument-description

Example:
# example-code
```
