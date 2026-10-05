# jinjacat - a simple script for expanding Jinja2 tags using front-matter.

## Rationale

I needed to build a diagram using graphviz. While working on it, I found
myself needing to specify colour values in multiple places. This concerned
me because I could see myself ending up needing to tweak colours, and this
would involve error-prone editing. It would be much easier if I could define
the colours at the start and use tags later in the file.

For some reason, I decided that Jinja2 tags and frontmatter was a nice way
of doing this, so that's what became jinjacat.

## Usage

    jinjacat [-unsafe] file [name=value [name2=value2 ...]]

This will process the contents of `file`, processing any definitions from
frontmatter and augmenting those definitions with any key=value pairs
specified on the command line. If `-unsafe` is specified and a `pipe` value
is defined, then the content is passed through `pipe` as a shell command.

If `-unsafe` is specified, then a key, `stdout` is automatically added to
the set of definitions, with the value set to Python's `sys.stdout`. This
allows your `pipe` definition to, for example, act conditionally on
`stdout.isatty()`.

## Example

See song.txt, which generates a song based on information in its front
matter.
