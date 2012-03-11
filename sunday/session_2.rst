Building A Python-Based Search Engine
=====================================

**Presenter:** Daniel Lindsley

**Track:** IV

**Description:**

    Search is an increasingly common request in all types of applications as the amount of data all of us deal with continues to grow. The technology/architecture behind search engines is wildly different from what many developers expect. This talk will give a solid grounding in the fundamentals of providing search using Python to flesh out these concepts in a simple library.

    https://us.pycon.org/2012/schedule/presentation/66/

Primary author of Haystack

**The Goal**

* teach you how search works
* increase your comfort with other engines

**Why should you care about search?**

* Standard crawlers have to scrape HTML
    * getting good content out of that can be a nightmare
* You know the data model better than they do
* Maybe it's not a web app at all

**Core Concepts**

* Document-based
    * never grep through a string
* Inverted Index

**Terms**

Engine - the black box you hand a query to get results back

Documents - a text blob with optional metadata

Corpus - the collection of all the documents

Stopword - words that are filler (and, the, of)

Steming - finding the root of the word

Segments - the data that make up the overall index

Relevance - the algorithm used to rank the results

Faceting - providing results matching a certain criteria

Boost - a way to push up certain type of results to the top

**Indexing**

* Documents
    * The are **not** a row in the db
    * think blob of text + metadata
    * text quality is the most important thing
    * flat, not relational
    * denormalize, denormalize, denormalize!!!!
* Tokenization
    * the process of taking the text blob and making it smaller word sized chunks
    * split on whitespace, lowercase, strip stopwords
    * the point is to normalize the tokens to work with when querying
* Stemming
    * the process of finding the root word
    * find root works because of spelling mistakes or pluralization
    * these become the terms in the inverted index
    * Cons: really only works on the language it was built for
    * very hard to make work cross language
    * how do we solve this? - n-grams
* n-grams
    * passes a "window" over the tokenized data
    * these become terms in the index
    * example gram size of 3 on hello
        * ['hel', 'ell', 'llo', 'wor', 'ld']
    * edge n-grams - typically uses multiple gram sizes
        * this works great for autocomplete
        * can also work across other languages
        * cons: generate a lot more terms and storage can be a problem
        * initially quality of search can suffer a little
* inverted index
    * the heart of the engine - it's how things work
    * like a dictionary - keys matter (terms from all docs)
    * stores position & document IDs
* Segments
    * with a huge data structure it really can't be in one file
    * lots of ways to do this
    * many follow Lucene
    * flat files and then hash the keys
    * terms will always be sorted
* Searching
    * Three main components
    * Query Parser
        * take a users hand written query and parse it out to something the engine can tackle
        * do this the same way as you do with the index
    * Index reading
        * per-term, hash the term to get the right file
        * rip through & collect position and document collection
    * Scoring
        * we have terms now, but the are out of order
        * lots of choices
            * bm25, phased, google's pagerank
* Faceting
    * for a given field, collect all terms
    * count the length of the unique document ids for each
    * order by descending count
* Boost
    * during the scoring process
    * If a condition is met, alter the score according
* More like this
    * collect all the terms for a given document
    * can find other like terms in other documents
    * sotr based on how many times a document is seen in the set
    * more complete solutions use NLP to increase quality

https://github.com/toastdriven/microsearch
http://speakerdeck.com/daniellindsley


