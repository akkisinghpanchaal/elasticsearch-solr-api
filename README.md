# elasticsearch Solr API

| Solr API | elasticsearch | Lucene/Solr |
|:--------:|:-------------:|:-----------:|
| develop  | 0.90.x        | 4.4.0       |
| master   | 0.90.5        | 4.4.0       |
| 1.2.2    | 0.90.5        | 4.4.0       |
| 1.2.1    | 0.90.3        | 4.4.0       |

## Overview

This plugin allows you to use elasticsearch with Solr interfaces.
The original project is [mocksolrplugin](https://github.com/mattweber/elasticsearch-mocksolrplugin), this project forked from it and was renamed in order to avoid confusion about each projects.

## Supported Solr features

* Update handlers
 * XML Update Handler (ie. /update)
 * JavaBin Update Handler (ie. /update/javabin)
* Search handler (ie. /select)
 * Basic lucene queries using the q paramter
 * start, rows, and fl parameters
 * sorting
 * filter queries (fq parameters)
 * hit highlighting (hl, hl.fl, hl.snippets, hl.fragsize, hl.simple.pre, hl.simple.post)
 * faceting (facet, facet.field, facet.query, facet.sort, facet.limit)
* XML and JavaBin request and response formats

## Install Solr API plugin

Type the following command:

    cd $ES_HOME
    ./bin/plugin -install org.codelibs/elasticsearch-solr-api/1.2.2

## How do you build this plugin?

Use maven to build the package

    git clone https://github.com/codelibs/elasticsearch-solr-api.git
    mvn package

Then install the plugin

    # if you've built it locally
    $ES_HOME/bin/plugin -url file:./target/releases/elasticsearch-solr-api-*.zip -install solr-api

## How to use this plugin.

Just point your Solr client/tool to your elasticsearch instance and appending /_solr to the url.

    http://localhost:9200/[index]/[type]/_solr

* [index] - the elasticsearch index you want to index/search against. Default "solr".
* [type] - the elasticsearch type you want to index/search against. Default "docs".
