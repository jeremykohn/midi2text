# Details #

  * Original release by Tim Thompson, tjt@twitch.att.com
  * 
  * June 1989 - Added writing capability, M. Czeiszperger.
  * 
  * Oct 1991 - Modifications by Piet van Oostrum <piet@cs.ruu.nl>:
  * Changed identifiers to be 7 char unique.
  * Added sysex write capability (mf\_w\_sysex\_event)
  * Corrected a bug in writing of tempo track
  * Added code to implement running status on write
  * Added check for meta end of track insertion
  * Added a couple of include files to get proper int=short compilation
  * 
  * Nov 1991 - Piet van Oostrum <piet@cs.ruu.nl>
  * mf\_w\_tempo needs a delta time parameter otherwise the tempo cannot
  * be changed during the piece.
  * 
  * Apr 1993 - Piet van Oostrum <piet@cs.ruu.nl>
  * decl of malloc replaced by #include <malloc.h>
  * readheader() declared void.
  * 
  * Aug 1993 - Piet van Oostrum <piet@cs.ruu.nl>
  * sequencer\_specific in midifile.h was wrong
  * 
  * Dec 2011 - Vaclav Spirhanzl <vaclav@spirhanzl.cz>
  * MAC OS X port, tested under 10.6.6, aka "Snow Leopard"
  * 
  * The file format implemented here is called
  * Standard MIDI Files, and is part of the Musical
  * instrument Digital Interface specification.
  * The spec is avaiable from:
  * 
  * International MIDI Association
  * 5316 West 57th Street
  * Los Angeles, CA 90056
  * 
  * An in-depth description of the spec can also be found
  * in the article "Introducing Standard MIDI Files", published
  * in Electronic Musician magazine, April, 1989.
  * 