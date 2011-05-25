Wow. Thanks for all the detailed responses. While I'll put together a more 
detailed entry over the weekend for my submission, my initial thoughts on 
hacking all the workflows I've seen on this list, with reference to 
transparency, etc.

First of all, Ian's daily(!) workflow (valid for any big newspaper) can be 
broken down as: (I hope the following ASCII diagram survives email clients)

Note: The numbers indicated are for labelling the stages, and are not really
indicative of any ordering.

------------------------------------------------------------------------------
                                        |
1)                                      |
Inception of an idea with a lot of back |
and forth between the editors and       | 2)
journalists.                            | Start obtaining photos
                                        |
3)                                      | 4)
The journalist starts working on his    | Contact media department/devs
report, contacting resources, etc.      | for visualizations, media.
                                        | 
5)			                | 7) Visualizations, media prepared
The reporter remains in contact with    |    according to data provided by
the editor about changes made to the    |    the reporter.
story and discuss it.                   |
					|
6)                                      |
The story might be discussed once again |
a few hours before the finishing time.  |
					| 9) 
8)                                      | Somewhere around this point the 
The reporter files the story and        | designers/devs submit requested
informs the editor, who reviews and     | media.
forwards it to the copy editor. Back    |
and forth between the editors and       | (Not necessarily approved/reviewed
journalist.                             |  by the editor or the journalist)
					|
------------------------------------------------------------------------------					

10) 
Paginator 'fits' the story into available space using available infographics,
photographs with back and forth with the journalist to strech or crop the 
article.

11)
The story finally goes for printing and is exported (somehow) to the website
(either by hand or by using a software, etc.)

12)
**REPEAT FROM 1**

------------------------------------------------------------------------------

I hope I've understood the workflow more or less correctly. Issues raised about
really being able to hack on this workflow involve getting this tech adopted,
cost and working with the existing legacy CMSs; apart from attempting together
improve transparency, crowdsourcing, etc.

Considering the vast amount of possible use cases, I'd say the requirements
can be broken down into, and solved by using a variation of tech.:

1. Managing and merging various discrete units of data while keeping a store
   of everything that has happened: a DVCS seems to be perfectly suited to
   this. Customized applications built on top of (Git)[http://git-scm.com][] 
   as the core would be able to manage the history of the creation and merging
   of any article.

2. Because of the existing CMSs and workflows at organizations, any solution
   we make must be completely atomic by stage of solution--it must be able
   to read in data from any source, and output data that can be consumed by any
   software with minimum work in conversion. This would ideally require a
   standard format along the lines of what Jake mentioned (Metadata for 
   news [http://www.buzzmachine.com/2009/07/11/metadata-for-news/][])--though
   the link to the actual specification seems to be broken.

   Something worked around JSON would be a rather elegant solution here,
   considering its readability and the availability of parsers. Having fixed
   formats also makes the process tool independent--every journalist can 
   work using his own favourite open source (perhaps) tool for each stage
   of work, a sort of mix-and-match which ensures consistency.

3. Essentially I'd propose a series of tools built around a central format for
   news data with all required metadata, fine grained control of access to 
   users (j,e) and subscribers, with options to suggest changes to the document
   with comments (like a bug issue tracker, for example).
  
   The tools -- with functionality -- I can imagine based on the workflows
   is:
   
     1. Wave-like tool that allows the journalists and the editors to
        collaborate; something that records the complete history of the 
	document as it is being edited (allowing a replay for interested
	people).

	The document will be configurable to allow for various sections a
	journalist can use: the initial idea and surrounding discussion,
	data the journalist collects from various sources, inputs FROM
	news subscribers, automated sources of data (like picking up a hashtag
	from twitter; or following a user, etc. -- automatically aggregating
        data from different sources -- so that 9 separate teams aren't required
	for aggregating information from a 5 day walk-about, as in Bill's case),
	photographs, finished/in progress visualizations, etc.

	Adding information will have to be platform agnostic--phone based 
	native applications to HTML5 based webapps to a headless browser
	running on journalist's computers. The views will based on the role of
	the person--copy editor/editor/journalist/paginator/photographer
	--based on their particular work requirements. 

     2. Simplified creation of visualizations and videos--again, using
        platform agnostic webapps that are configured to consume most APIs
	and built around the article metadata standard. Something that could
	be used as a base for designers/developers at news agencies for rapid
	prototyping and then building upon; and relatively standard
	infographics that can be directly created by journalists without 
	having to touch a line of code.

   With fine grained permissions, large parts of the history of an article
   can be made public for comments, further discussion and possibly newspaper
   articles.

      3. Content Exporter/Importer: A way to move the standard format to any
         of the CMS's; say, for example a WordPress importer. The same article
	 can be published to a wiki, to wordpress, drupal or anywhere you care
	 to name as required.

This is just an initial draft written by me while almost falling asleep, so 
please forgive typos, etc. What do you think--have I covered most of the 
requirements--suggestions, technical and otherwise?

-Kunal
