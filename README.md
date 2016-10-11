** Introduction ** 

This is my own personal notes on what I've found out on the web for beginning to consider hypermedia approaches for linking data. I've relied on the wider community for their advice and findings and so I hope others will find this page a handy one stop shop. 

** Acknowledgements ** 

* [Niels Krijge Handy Comparsion Table ](http://www.nielskrijger.com/#!/posts/2014-08-05-choosing-a-hypermedia-type.html) 
* [Kevin Sookocheff](https://sookocheff.com/post/api/on-choosing-a-hypermedia-format/)
* [Mike Stowe](http://blogs.mulesoft.com/dev/api-dev/api-best-practices-hypermedia-part-3/)  


** Taken from Niels Krijge Blog **

Legend can be found [here](http://www.nielskrijger.com/#!/posts/2014-08-05-choosing-a-hypermedia-type.html#hypermedia-specification-comparison)

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
Taken from Mike Stowes blog. 


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





