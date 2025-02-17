# asm-parser

Categorises and filters assembly in a way that's understood by Compiler Explorer.

Possible filters as command line parameters:

* `-binary` changes to the Binary mode filtering that's based on the assembly output from GNU Objdump
* `-unused_labels` try to filter out functions that aren't strongly used
* `-directives` filter out .directives
* `-comment_only` filter out comments
* `-whitespace`
* `-library_functions` try to filter out functions that belong in other libraries that are used (filtering is based on filepaths)
* `-dont_mask_filenames` always output the filename if available

Other parameters:

* `-plt` Also leaves out labels that End with `@plt` (without this, only labels that Start with `.plt` are left out)
* `-nocompat` Leaves some experimental extra information
* `-stdin` Reads assembly from STDIN instead of from a given file
* `-outputtext` Instead of writing to JSON, output the filtered assemblys


### Example usage

Feeding an objdump via stdin into asm-parser:

`objdump --d a.out -l --insn-width=16 | asm-parser -stdin -binary`
