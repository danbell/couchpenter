Couchpenter [![http://travis-ci.org/cliffano/couchpenter](https://secure.travis-ci.org/cliffano/couchpenter.png?branch=master)](http://travis-ci.org/cliffano/couchpenter)
-----------

Couchpenter is CouchDB database and document setup tool.

Installation
------------

    npm install -g couchpenter 

Usage
-----

Create setup file example:

    couchpenter init

Set up databases and documents:

    couchpenter setup -u http://user:pass@localhost:5984 -f ./couchpenter.json

Programmatically:

    var couchpenter = new require('couchpenter').Couchpenter();
    couchpenter.setUp('http://user:pass@localhost:5984', './couchpenter.json', process.cwd(), function (err) {
      // do something
    });

Configuration
-------------

Couchpenter setup file is a just a simple JSON file containing:

    {
     	"db1": [
     	  { "_id": "doc1", "foo": "bar" },
     	  { "_id": "doc2", "foo": "bar" },
     	  "path/to/doc3file.json"
     	],
     	"db2": [
        { "_id": "doc4", "foo": "bar" },
        "path/to/modulename"
     	],
      "db3": []
    }

Property keys are the names of the databases that should exist in CouchDB. If a database does not exist, it will then be created.

Property values are the documents that should exist in each database. If the document does not exist, it will then be created. If it already exists, it will then be updated.

A document can be represented as:

* an object
* a file path string containing a JSON document, file name must end with .json
* a module path string

Paths are relative to current directory if it's used from command-line, or relative to setUp() dir if it's used programmatically.

Colophon
--------

Follow [@cliffano](http://twitter.com/cliffano) on Twitter.
