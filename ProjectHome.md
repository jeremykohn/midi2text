## Programs for conversion standard midifiles from and to text format. ##

**mf2t** is a program that reads a _standard midifile (format 0 or 1)_ and
writes an ASCII representation of it that is both compact and easily parsable.

**t2mf** is the companion program that reparses the text representation
into a _midifile_.

The text representation is chosen such that it is easily recognized and
manipulated by programs like _sed, awk or perl_. Yet it is also humanly
readable so that it can be manipulated with an ordianary text editor.

Both programs are described in detail [here](ProgDescription.md) and generated text format [here](TextFormatDescr.md).

History of [MIDI file library](MidiFileLibDescr.md).

MAC OS X port from Vaclav Spirhanzl , tested under MAC OS X 10.6.6, <br />
Windows version is located on http://www.midiox.com