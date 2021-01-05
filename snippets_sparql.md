## meaning
spaql  protocol and pdf query language (recursive)

## query

SELECT ?s ?p ?o
WHERE { ?s ?p ?o } -- returns everything in database

to select certain columns:
SELECT ?royal ?age
WHERE { ?royal <../hasAge> ?age }

to select by value of columns:
SELECT ?royal ?title
WHERE { ?royal <../hasAge> 68 .
		?royal <../hasTitle ?title .
}

**note the full-stop '.' after each statemnt**

get number of rows:
SELECT (COUNT(?s) as ?numTriples)
WHERE { ?s ?p ?o }

get value counts:
SELECT ?class (COUNT(?subject) as ?classCount)
WHERE {
	?subject ?predicate ?object.
	?subject rdf:type ?class .
}
GROUP BY ?class
ORDER BY DESC(?classCount)

get songs that James Taylor sings
SELECT ?song
WHERE { :James_Taylor :sings ?song . }

## actual examples

SELECT ?planet ?type ?abstract
WHERE {
?planet rdf:type ?type .
?type rdfs:label "planet"@en .
?planet dbo:abstract ?abstract .
FILTER(lang(?abstract) = "en")
} LIMIT 10
## rdf and syntax

triples look like
(subject, predicate, object)
eg (charles, :hasAge, 68)

- one of more triple patterns together form a basic graph pattern (BGP)

rdf file:
@prefix prop: <https://example.com/properties/>
@prefix royFam: <https://royalfamily.com/>
royFam:charles prop:hasAge 68 .
royFam:charles prop:hasTitle "Prince of Wales" .
...

## prefixes

in query prefix looks like:
PREFIX foo: <http ...>

common
- rdf: xmins
- foaf: same as rdf
- owl: w3
- xsd: w3 xml
- dbo: dbpedia ontology
- dc: purl.org/dc/elements

## construct query
makes rdf triples or graph

CONSTRUCT {
	?country a ex:HolidayDesimation ;
		ex:arrive_at ?capital ;
		ex:population ?population
}

## patterns
{ A } UNION { B } has results fitting A and also results fitting B



## describe query
DESCRIBE ?country

## ask query
ask whether or not there are any matches

## endpoints
dblp (cs journals)
world factbook from cia
bio2rdf bioinformatics

## book notes

turtle is an rdf format (.ttl file)
store sparql queries in .rq file

URI: uniform resource identifier eg http://w3.org#justin
URL: uniform resource locator

"i want these pieces of information from the subject of the data that meets these conditions"

then describe the conditions with **triple patterns**

patterns are similar to pdf triples, but can include variables for broader use

SELECT ?craigEmail # at this point craigEmail does not exist but we defined it to be a variable
WHERE {ab:craig, ab:email ?craigEmail}

Jena ARQ tool to execute query
[in cmd or git] arq --data triples.ttl --query my_query.rq

can specifc data source in query:
SELECT ?craigEmail FROM <triples.ttl> WHERE { ...}

"i want to find people who have the telephone number 12345"
SELECT ?person
WHERE { ab:person ab:homeTel 12345}

"i want to list everything i can get on Cindy"
SELECT ?propertyName
WHERE {ab:cindy ?propertyName ?propertyValue . }

so we don't specifc any resource for the 2nd and 3rd values but rather a variable, telling sparql that anything is okay

for the above we assume both the names and emails come from the data data source. now let's assume names, emails, etc come from ab (addressbook) and the identified comes from another data source (d)

"i want to find craig's email address"
SELECT ?craigEmail
WHERE {
	?person ab:firstName "Craig" .
	?person ab:email ?craigEmail .
}

multiple clauses allow you to search for multiple triple types across different data sources. "queries aren't as closely tied to specific data structures as they are with a query language like sql"

when you see examples with SELECT ?s ?p ?o you now know those are arbitrary variables

can filter with regex
SELECT *
WHERE {
	?s ?p ?o
	FILTER(regex(?o, "yahoo", "i"))
}
checks if "yahoo" in object (ie email)
last parameter means case insensitive

in snorql, dbpedia/resource has prefix of ":" which is why you see names like :Timberland

normally using a resource in the subject and object and an ontology in the predicate

tim berners-lee behind much of the web including w3 and rdf/owl/sparql and html and http and url's. he also wrote the first web server.

IRI: internationalized resouce identifers
can have chinese or other characters

in rdf, a subject and predicate must be URI's

N-triples (.nt) allows for whitespace
N3 (.n3) does not allow for whitespace

triplestore is a database for rdf

in turtle, can add datatype to object with ^^obj_type_uri after

d:item2 dm:shipped   "2011-02-14"^^xsd:date

also have language labels
d:item2 dm:title   "elmo toy"@en


