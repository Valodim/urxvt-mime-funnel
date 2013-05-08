urxvt-mime-funnel
=================

This is a perl extension for rxvt-unicode, inspired by
[HTerm](http://41j.com/hterm/). What it basically does is react to a specific
OSC code, intercepts the following base64 encoded data (which would otherwise
be rendered as text), and displays it according to the given mimetype.

Trying this manually would look something like this:
	printf "\033]777;mime-funnel;image/png;\007" ; base64 image.png ; echo '!'

So why is this useful? Because it allows displaying arbitrary, base64 encoded
media from a console stream, in particular over ssh with no server-side
dependencies whatsoever.

The script uses base64 for decoding, and run-mailcap (packaged in debian with
mime-support) to run an appropiate application for the mimetype. See man 5
mailcap.

Installation
------------

To install, simply copy (or symlink) the mime-funnel script into your urxvt
perl-lib directory, and add it to your list of perl-exts. In an .Xresources,
this would look as follows:

	URxvt.perl-lib: /path/to/other/stuff:/path/to/repo
	URxvt.perl-ext: mime-funnel

Or to just give it a whirl, run urxvt as such:
	urxvt --perl-lib /path/to/repository -pe mime-funnel

You can then use the supplied *funnel* script to display data in this way, or
any other way using the interface described above.

