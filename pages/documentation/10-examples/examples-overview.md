---
title: Examples Overview
keywords: examples
last_updated: September 23, 2016
tags: [getting-started, examples]
summary: "Landing page for Grakn examples."
sidebar: documentation_sidebar
permalink: /documentation/examples/examples-overview.html
folder: documentation
comment_issue_id: 27
---


## Introduction

This page lists the examples of Grakn that we suggest you study to learn how to work with our stack.  We plan to continue to expand our set, and we also encourage you to let us know if you have example code to share, so we can link to it (for example, to your repo or a blog post).

If you would like to request a particular example, please get in touch with us by leaving a comment on this page or posting a question on the discussion boards.  Our [Community page](https://grakn.ai/community.html) lists other ways you can talk to us.

### Genealogy Dataset

The genealogy dataset is widely used across our documentation about GRAKN.AI, because it allows for a simple, yet powerful, illustration of many key features. As described below, it is used to illustrate CSV migration and the Grakn Reasoner.

It is available on the [sample-datasets repo on Github](https://github.com/graknlabs/sample-datasets/tree/master/genealogy-graph), and is also discussed in the ["Family Matters" blog post](https://blog.grakn.ai/family-matters-1bb639396a24#.4gnoaq2hr). 

### [Modern](./modern.html)

The [Modern example](./modern.html) is a simple one, designed to test your knowledge of Graql.

### [OWL Migration](./OWL-migration.html)

For more information about migrating OWL to Grakn, please see the [OWL migration example](../examples/OWL-migration.html).

### SQL Migration

A common use-case is to migrate existing SQL data to a graph in Grakn. We walk through a simple example of using the migration script as part of the documentation about [SQL migration](../migration/SQL-migration.html), and there is a further example of [SQL migration using the Java API](../examples/SQL-migration.html). We also cover SQL migration in a [blog post](https://blog.grakn.ai/populating-mindmapsdb-with-the-world-5b2445aee60c#).

### CSV Migration

We use the genealogy dataset to show [how to migrate genealogy data into Grakn from CSV](../examples/CSV-migration.html). 

Our [sample-projects repository on Github](https://github.com/graknlabs/sample-projects) also contains [an example that takes a simple CSV data file of pets](https://github.com/graknlabs/sample-projects/tree/master/example-csv-migration). Please see the [readme file](https://github.com/graknlabs/sample-projects/blob/master/example-csv-migration/README.md) to get started.

CSV migration is also covered in a [blog post](https://blog.grakn.ai/twenty-years-of-games-in-grakn-14faa974b16e#.cuox3cew2).


### Grakn Reasoner

We use the genealogy dataset to illustrate how to write rules to infer new information from a dataset. You can find the example [here](./grakn-reasoner.html).

### R and Python bindings
It is possible to extract data from Grakn and use it as a data science tool for analysis. You can take the results of a Graql query and store the results in a dataframe or similar structure, for use with R or Python. This [blog post](https://blog.grakn.ai/there-r-pandas-in-my-graph-b8b5f40a2f99#) explains and gives a simple example. A further [blog post](https://blog.grakn.ai/grakn-pandas-celebrities-5854ad688a4f#.k5zucfp6f) uses the Python driver to examine our example movie dataset.


### Pokemon

The Grakn repo on Github contains [pokemon.gql](https://github.com/graknlabs/grakn/blob/master/grakn-dist/src/examples/pokemon.gql), which is a simple example to illustrate a basic ontology and dataset. It is currently used in our Graql documentation to illustrate how to form a range of different Graql queries.

### Philosophers

The Grakn repo on Github contains [philosophers.gql](https://github.com/graknlabs/grakn/blob/master/grakn-dist/src/examples/philosophers.gql), which contains a simple ontology and data, for use as an example.

The [sample-projects](https://github.com/graknlabs/sample-projects) repo on Github contains a Java project that uses the Java Graph API on the same data and ontology. 

### Moogi Movie Database

[Moogi](https://moogi.co) is a large database of information about movies. We have provided a subset of its data to try out in our [sample-datasets repository](https://github.com/graknlabs/sample-datasets/tree/master/movies) on Github.

## Where Next?

If you are interested in writing an example on Grakn, maybe as a way of trying it out, please take a look at the [Example Projects](./projects.html) page, which lists some ideas that we have for potential examples or research projects.


{% include links.html %}


## Comments
Want to leave a comment? Visit <a href="https://github.com/graknlabs/docs/issues/27" target="_blank">the issues on Github for this page</a> (you'll need a GitHub account). You are also welcome to contribute to our documentation directly via the "Edit me" button at the top of the page.

