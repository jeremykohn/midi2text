# Introduction #

**mf2t** is a program that reads a standard midifile (format 0 or 1) and
writes an ASCII representation of it that is both compact and easily parsable.

**t2mf** is the companion program that reparses the text representation
into a midifile.

The text representation is chosen such that it is easily recognized and
manipulated by programs like sed, awk or perl. Yet it is also humanly
readable so that it can be manipulated with an ordianary text editor.

In this way you can make changes to your midifiles using these
powerful programs or even a Fortran program :=). Or you can write
algorithmic compositions using a familiar programming language.

The programs use the midifile library written by Tim Thompson
(tjt@blink.att.com) and updated by Michael Czeiszperger (mike@pan.com).
However, there were some bugs in the write code and I added some
features that I needed. I also changes some of the names to cope with
the 7-character limit for external identifiers in the Sozobon
compiler. I will make an updated version of the library available
soon. I also anticipate to split the read and write portions.

# Usage #

> _mf2t [-mntv] [-f[n](n.md)] [[textfile](midifile.md)]_<br />

> translate midifile to textfile.<br />

When textfile is not given, the text is written to standard output.<br />
When midifile is not given it is read from standard input. The meaning
of the options is:<br />

-m	merge partial sysex into a single sysex message<br />
-n	write notes in symbolic rather than numeric form. A-C optionally followed by # (sharp) followed by octave number.<br />
-b	   or<br />
-t	event times are written as bar:beat:click rather than a click number<br />
-v	use a slightly more verbose output<br />
-fn	fold long text and hex entries into more lines n=line length (default 80).<br />
-h   displays this help<br />

> _t2mf [-r] [[textfile](textfile.md) midifile]_<br />

> translate textfile to midifile.<br />

When textfile is not given, text is read from standard input, when midifile is not given it is written to standard output.

-r	Use running status<br />

Note that if one file is given it is always the midifile. This is so
that on systems like Unix you can write a pipeline:<br />

> mf2t x.mid | sed ... | t2mf y.mid

## input ##

**t2mf** will accept all formats that **mf2t** can produce, plus a number of others.
Input is case insensitive (except in strings) and extra tabs and
spaces are allowed. Newlines are required but empty lines are allowed.
Comment starts with # at the beginning of a lexical item and continues
to the end of the line. The only other places where a # is legal are
insides strings and as a sharp symbol in a symbolic note.

In symbolic notes + and # are allowed for sharp, b and - for flat.

In bar:beat:click time the : may also be /

On input a string may also contain \t for a tab, and in a folded
string any whitespace at the beginning of a continuation line is skipped.

Hex sequences may be input without intervening spaces if each byte is
given as exactly 2 hex digits.

Hex sequences may be given where a string is required and vice versa.

Hex numbers of the form 0xaaa and decimal numbers are equivalent.
Also allowed as numbers are "bank numbers" of the form '123. In fact
this is equivalent to the octal number 012 (subtract 1 from each
digit, digits 1-8 allowed). The letters a-h may also be used for 1-8.

The input is checked for correctness but not extensively. An
errormessage will generally imply that the resulting midifile is illegal.