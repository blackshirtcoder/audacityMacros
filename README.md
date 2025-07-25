# Audacity Macros

This repository contains a few custom macros I've written for Audacity,
the open-source, multi-platform audio file editor.

The macros are stored as plain text files in `~/code/audacityMacros` and
are symlinked into `~/.audacity-data/Macros` so that Audacity can use
them directly.

## Included Macros

- `Audiobook.txt`: Designed to batch process a series of audio files
  that, taken together, constitute the complete text of an
  audiobook. Usually these individual files will correspond to, say, the
  content of one book CD or one side of a book cassette. The macro
  converts the audio to mono, performs click removal, performs
  compression to normalize to the audio to a reasonable volume level
  without clipping, and, finally, exports the massaged audio to a .wav
  file. Other tools in my tool chain are then used to concatenate the
  audio files into one, long, continuous book file for further
  processing (like cutting into individual chapter files with Audacity).

- `ChapterFadeInAndTrim.txt`: This macro assists with the task of taking
  an audio file that contains the complete text of an audiobook and
  splitting it into individual book segments. A "book segment", in this
  context, is usually the contents of one book chapter, but can be other
  things like a forward, an epilogue, an introduction, a dedication,
  etc. For all my books, I want each segment to begin with 0.5 seconds
  of silence. This macro expects the cursor to begin right at the start
  of the segment. To the left would normally be a silent region. It
  fades in the first 0.5 seconds of that silence, and everything else to
  the left it deletes.

- `ChapterFadeOutAndSelect.txt`: This is the counterpart to
  `ChapterFadeInAndTrim`. When separating out book segments as described
  above, I want all my segments to end with 1.0 seconds of silence. To
  use this macro, it is expected that the cursor starts right at the
  very end of the non-silent audio of the segment and that there is at
  least 1 second of "silence" to the right of it. The macro selects a 1
  second region to the right, fades it out, then selects that region as
  well as everything up to the beginning of the file. Once done, the
  entire segment (a chapter or whatever) will be selected and can be
  saved to disk.

## Usage

To install:
1. Clone this repo to `~/code/audacityMacros`
2. Create symlinks in `~/.audacity-data/Macros/` pointing to the files in this repo.

```bash
ln -s ~/code/audacityMacros/Audiobook.txt ~/.audacity-data/Macros/Audiobook.txt
