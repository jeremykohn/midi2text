# Details #
The following representation of the midievents is generated (between
[.md](.md) the form when -v is used:
```
File header:		Mfile <format> <ntrks> <division>
Start of track:		MTrk
End of track:		TrkEnd

Note On:		On <ch> <note> <vol>
Note Off:		Off <ch> <note> <vol>
Poly Pressure:		PoPr[PolyPr] <ch> <note> <val>
Channel Pressure:	ChPr[ChanPr] <ch> <val>
Controller parameter:	Par[Param] <ch> <con> <val>
Pitch bend:		Pb <ch> <val>
Program change:		PrCh[ProgCh] <ch> <prog>
Sysex message:		SysEx <hex>
Arbutrary midi bytes:	Arb <hex>

Sequence nr:		Seqnr <num>
Key signature:		KeySig <num> <manor>
Tempo:			Tempo <num>
Time signature:		TimeSig <num>/<num> <num> <num>
SMPTE event:		SMPTE <num> <num> <num> <num> <num>

Meta text events:	Meta <texttype> <string>
Meta end of track:	Meta TrkEnd
Sequencer specific:	SeqSpec <type> <hex>
Misc meta events:	Meta <type> <hex>

The <> have the following meaning:

<ch>		ch=<num>
<note>		n=<noteval>  [note=<noteval>]
<vol>		v=<num> [vol=<num>]
<val>		v=<num> [val=<num>]
<con>		c=<num> [con=<num>]
<prog>		p=<num> [prog=<num>]
<manor>		minor or major
<noteval>	either a <num> or A-G optionally followed by #,
		followed by <num> without intermediate spaces.

<texttype>	Text Copyright SeqName TrkName InstrName Lyric Marker Cue
		or <type>
<type>		a hex number of the form 0xab
<hex>		a sequence of 2-digit hex numbers (without 0x)
		separated by space
<string>	a string between double quotes (like "text").

Channel numbers are 1-based, all other numbers are as they appear in
the midifile.
<division> is either a positive number (giving the time resolution in
clicks per quarter note) or a negative number followed by a positive
number (giving SMPTE timing).
<format> <ntrks> <num> are decimal numbers.
The <num> in the Pb is the real value (two midibytes combined)
In Tempo it is a long (32 bits) value. Others are in the interval 0-127
The SysEx sequence contains the leading F0 and the trailing F7.

In a string certain characters are escaped:
" and \ are escaped with a \
a zero byte is written as \0
CR and LF are written as \r and \n respectively
other non-printable characters are written as \x<2 hex digits>
When -f is given long strings and long hex sequences are folded by inserting
\<newline><tab>. If in a string the next character would be a space or
tab it will be escaped by \
This facility is for those programs that have a limited buffer length.
Of course parsing is more difficult with this option .
```