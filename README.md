hoosing a Hypermedia Type: HAL vs JSON-LD vs Collection+JSON vs Siren vs JSON API 

Take from 

* http://www.nielskrijger.com/#!/posts/2014-08-05-choosing-a-hypermedia-type.html
* https://sookocheff.com/post/api/on-choosing-a-hypermedia-format/
* http://blogs.mulesoft.com/dev/api-dev/api-best-practices-hypermedia-part-3/ 
* Daisy Chaining - http://www.networkworld.com/article/3127356/cloud-computing/daisy-chaining-apis-makes-serverless-sense.html


<table class="table table-striped small">

<tbody>

<tr>

<th>Hypermedia Type</th>

<th>Primary keywords</th>

<th>Embedded resources</th>

<th>Single object wrapper</th>

<th>Documentation links</th>

<th>Pagination</th>

<th>Sorting</th>

<th>Error</th>

<th>Partial updates</th>

<th>Query</th>

<th>Actions</th>

<th>Partial result</th>

<th>Matches vanilla</th>

</tr>

<tr>

<td>JSON:API</td>

<td>id, links, meta, linked, type, href</td>

<td>Yes</td>

<td>In array</td>

<td>No</td>

<td>No</td>

<td>Yes</td>

<td>Yes</td>

<td>PATCH</td>

<td>No</td>

<td>No</td>

<td>Yes</td>

<td>3/5</td>

</tr>

<tr>

<td>HAL</td>

<td>_links, _embedded, curies</td>

<td>Yes</td>

<td>No</td>

<td>Yes</td>

<td>Minimal</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>4/5</td>

</tr>

<tr>

<td>Collection+JSON</td>

<td>links, collection, items, href, data, queries, template, version, error</td>

<td>No</td>

<td>In array</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>Yes</td>

<td>Write representations</td>

<td>Yes</td>

<td>No</td>

<td>Yes</td>

<td>2/5</td>

</tr>

<tr>

<td>Siren</td>

<td>class, properties, entities, links, actions, title, rel, href, type</td>

<td>Yes</td>

<td>In properties</td>

<td>No</td>

<td>Minimal</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>Yes</td>

<td>Yes</td>

<td>No</td>

<td>2/5</td>

</tr>

<tr>

<td>JSON+LD</td>

<td>@context, @id, @value, @language, @type, @container, @list, @graph ...</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>No</td>

<td>3/5</td>

</tr>

</tbody>

</table>



**JSON API**  

*Strengths*
	
* simple versatile format 
* easy to read / implement 
* wide adoption
* strong community 
* recognized as IANA media type 
* designed to be less chatty "without compromising readability, flexibility and discoverability" 
* backward compatibile 
* lots and lots of implementations in a variety of languages 



*Weaknesses* 

* forces you to identify resources with the reserved keyword 'id' so limits more advanced uses cases of compound keys 
* JSON only
* still WIP 
* no documentation links - whether the hypermedia type specifies how to access human readable documentation of a resource.

**HAL** 

*Strengths*

* dynamic - what does this mean? does this mean data inclded in the response to describe an object 
* nestable
* easy to read / implement 
* multi-format - XML / JSON 
* URL templating 
* inclusion of documentation links - HAL is the only one to support this 
* wide adoption 
* strong community 
* recognized as a standard 
* RFC proposed 

*Weaknesses* 

* JSON/XML formats architecturally different 
* CURIEs are tightly coupled 



** JSON-LD ** 

*Strengths*

* strong format for data linking
* can be used across multiple data formats (Web API & Databases) ? huh?
* strong community
* large working group
* recognized W3C standard 
* JSON-y so client devs will find it familar 
* can add actions to it with Hydra (still WIP)
* SPARQL support 


*Weaknesses*

* JSON only - how to get around this? 
* more complex to integrate 
* no identifier for documentation - how to do this? 
* limited support for pagination, sorting, error, partial updates, query, actions etc  









**How to approach pagination in JSON-LD** 


https://www.w3.org/community/hydra/wiki/Collection_Design





Collection+JSON specifies search/filter queries (and is designed for CRUD, of course), but not really “workflow” queries. HAL seems to be more open in this regard (with various “_links”). Siren explicitly specifies “actions”, which is the clearest IMO.


I find that specifying linked objects by their URI is very cool and desirable when it comes to GET-ing data. But slightly less cool when it comes to  setting it, in that in mandates the server to parse a full URL in order to do the usual stuff of storing some ref id in a column of a database. For instance, say a HAL “order” has a “_link” to “customer” : { "href": “http://host/customers/1234” }. It would be easier for the server to handle a store/update request with some kind of “customer”: { “id”: 1234 }, instead of parsing "href": “http://host/customers/1234”. But I understand it would break the homogeneity of the API and can live with it, of course.

can we export into triples? 

JSON-LD serialiser -> application/nquads (triplestore)
