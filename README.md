# GenDocs

## Description

Simple documentation generator for AWK.

## Requirenments

- `GNU Awk 5.0.1`

## Syntax

`awk -f gendocs.awk -- <input-awk-files>`

where `<input-awk-files>` - set of `.awk` files to parse and generate documentation from.

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
```awk
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

```
# AWK-file-name-without-extension

## function-name(argument-type)

Description.

Arguments:
- `argument-name`: argument-type - argument-description

Example:
# example-code
```
