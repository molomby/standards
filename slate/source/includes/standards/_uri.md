## URI Structure

>Some example URIs that meet this standard are:  
`http://www.bank.com.au/api/cds-au/v1/banking/accounts`  
`http://www.bank.com.au/complex/uri/taxonomy/cds-au/v1/banking/products`  
`http://www.energyretailer.com.au/api/cds-au/v1/energy/usage`

The URI structure for API end points in the standards MUST be implemented as follows:  
`<holder path> / cds-au / <version> / <industry> / <resource>`

The components of this URI structure are described as follows:

* **Holder Path**: The holder path is a base path set by the data holder. It can be any URI desired by the holder. While all authenticated end points must be accessible under the same holder path the data holder may stipulate a different holder path for unauthenticated end points.
* **“cds-au”**: This is a static string representing the end points defined by the Consumer Data Standards for Australia. This static string allows for separation from other APIs available at the same base holder path and also allows for extension if the standards are adopted by another jurisdiction in whole or in part.
* **Version**: The major version of the high level standards. This is not the version of the endpoint or the payload being requested but the version of the overall standards being applied. This version number will be “v” followed by the major version of the standards as a positive integer (e.g. v1, v12 or v76).
* **Industry**: A static string used to separate APIs for a specific industry. As standards for new industries are defined the list of industry strings will be extended.
* **Resource**: The URI for the specific resource requested. This end point URI will be defined as part of the end point definitions for each API group.

Note that the currently accepted values for the `Industry` component of the base path are:

* **banking** – for APIs related to banking and potentially wider financial services data
* **energy** – for APIs related to the energy distribution industry
* **telco** – for APIs related to telecommunications
* **common** – for APIs that potentially span industries

### Resource URIs

Resources that are collections, and members of collections, will follow the [JSONAPI.org](http://jsonapi.org) recommendation.

Under this model, collections, individual members and collection sub-resources would be accessed as follows:

[]() | []()
-|-
`GET …\accounts` | Returns an array of accounts
`GET …\accounts\{id}` | Returns the detail of a specific account
`GET …\accounts\transactions` | Returns the transactions of multiple accounts
`GET …\accounts\{id}\transactions` | Returns the transactions of a specific account
`POST …\accounts` | Create a new account
`POST …\accounts\search` | Returns an array of accounts based on a complex query

The final example above represents a complex query accessed via a POST request.  In this situation the POST URI should be applied to a sub-resource of the collection.  A POST to a collection is reserved for the creation of a new collection member.

If no valid sub-resource exists then a dedicated sub-resource should be created, such as the “search” URI listed in the example above.
