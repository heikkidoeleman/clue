CLue - Command Line tool for Apache Lucene
==========================================

### Overview:

When working with Lucene, it is often useful to inspect an index.

[Luke](http://www.getopt.org/luke/) is awesome, but often times it is not feasible to inspect an index on a remote machine using a GUI.

Another important feature for Clue is the ability to interact with other Unix commands via piping, e.g. grep, more etc.

### Build:

mvn package

### Run:

Interactive Mode:

    ./bin/clue.sh my-idx

Non-interactive Mode:

    ./bin/clue.sh my-idx command args

Command list:

    ./bin/clue.sh my-idx help


    delete - deletes a list of documents from searching via a query, input: query
	docval - gets doc value for a given doc, <field> <docid>, if <docid> not specified, all docs are shown
	exit - exits program
	help - displays help
	info - displays information about the index, <segment number> to get information on the segment
	merge - force merges segments into given N segments, input: number of max segments
	postings - iterating postings given a term, e.g. <fieldname:fieldvalue>
	search - executes a query against the index, input: <query string>
	terms - gets terms from the index, <field:term>, term can be a prefix
	

### Examples:

1. Getting all the terms in the field 'color':

    **./bin/clue.sh /tmp/my-idx terms color**

2. Getting all the terms in the field 'color' starting with the term staring with 'r':

    **./bin/clue.sh /tmp/my-idx terms color:r**

    **./bin/clue.sh /tmp/my-idx terms color | grep r**

3. Do a search:

    **./bin/clue.sh /tmp/my-idx search myquery**

4. Get the index info:

    **./bin/clue.sh /tmp/my-idx info**

5. Iterate a posting for the term color:red

    **./bin/clue.sh /tmp/my-idx postings color:red**

6. List docvalues for a column-stride-field:

    **./bin/clue.sh /tmp/my-idx docval price**
