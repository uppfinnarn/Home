About
-----
This is what I use to run <http://macaronicode.se>.

Feel free to steal anything (especially fileblog.py) for yourself. There's no license.

Requirements
------------
* Python 2.7
	* flask
	* markdown2
	* jsonpickle

Idea
----
I'm not a big fan of databases. When I wrote the very first version of this site, I used a database, but it seemed silly and overkill for something that doesn't actually need to store more than static text. Static text is what you have static text files for, right?

So, I made a blog platform using only static text files. Posts are written using Markdown, metadata is stored using Markdown2's `metadata` extension, and are thus fully human-readable and safe from database corruption/crashes.

Post Syntax
-----------
Fileblog puts only one constraint on your post syntax: the first non-blank line (after an eventual [metadata block](http://hiltmon.com/blog/2012/06/18/markdown-metadata/)) must be a title (underlined with =====).

Also, since file modification timestamps are rather fragile things (a simple `touch` or move is enough to reset it) and only Mac OS X stores creation time, Fileblog needs to store the timestamp in the file.
This is done with a line like `! 27 Apr 2013, 15:14` inserted at the start of a file upon first viewing it.  
I recommend you to create a blank file, view it to get an autogenerated timestamp, then open and edit it. Before publishing, remember to delete the old timestamp and view it to get a new one. And not to overwrite the new one by saving over it.

I get HTTP 500:s everywhere in production!
------------------------------------------
Make sure the `cache` directory is writable by the web server. It'll probably default to be writable only by you.
