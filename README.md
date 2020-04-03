EWP Mobility Factsheet API
==========================

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

This document describes the **Mobility Factsheet API**. This API allows partners to share
all the information useful for incoming students in the mobility process.
**This API is still in progress.** In particular, the content of the response does not yet correspond fully to the
[Interinstitutional Agreement template](https://github.com/erasmus-without-paper/ewp-specs-api-iias/blob/stable-v2/resources/template_EuropeanCommission_IIA_21-29.pdf).


Request method
--------------

 * Requests MUST be made with either HTTP GET or HTTP POST method. Servers MUST
   support both these methods. Servers SHOULD reject all other request methods.

 * Clients are advised to use POST when passing large number of parameters
   (servers MAY set a limit on their GET query string length).


Request parameters
------------------

Parameters MUST be provided in the regular `application/x-www-form-urlencoded`
format.


### `hei_id` (repeatable, required)

A list of institution identifiers (no more than `<max-hei-ids>` items) - IDs of
HEIs the client wants to retrieve information on.

This parameter is *repeatable*, so the request MAY contain multiple occurrences
of it. The server is REQUIRED to process all of them.

Server implementers provide their own chosen value of `<max-hei-ids>` via their
manifest entry (see [manifest-entry.xsd](manifest-entry.xsd)). Clients SHOULD
parse this value (or assume it is equal to `1`).

Clients may retrieve proper HEI identifiers from other EWP APIs (most often,
the [Registry Service][registry-spec]). Servers MUST be able to accept all HEI
IDs declared in their [manifest files][discovery-api].


Security
--------

This version of this API uses [standard EWP Authentication and Security, Version 2][sec-v2].
Server implementers choose which security methods they support by declaring them in their Manifest API entry.


Handling of invalid parameters
------------------------------

 * General [error handling rules][error-handling] apply.

 * Invalid (unknown) `hei_id` values MUST be **ignored**. Servers MUST return
   a valid (HTTP 200) XML response in such cases, but the response will simply
   not contain the information on the unknown `hei_id` values. If all values
   are unknown, servers MUST respond with an empty `<factsheet-response>` element.
   This requirement is true even when `<max-hei-ids>` is equal to `1`.

 * If the length of `hei_id` list is greater than `<max-hei-ids>`, servers
   MUST respond with HTTP 400.


Response
--------

Servers MUST respond with a valid XML document described by the
[response.xsd](response.xsd) schema. See the schema annotations for further
information.



[develhub]: http://developers.erasmuswithoutpaper.eu/
[discovery-api]: https://github.com/erasmus-without-paper/ewp-specs-api-discovery
[error-handling]: https://github.com/erasmus-without-paper/ewp-specs-architecture#error-handling
[registry-spec]: https://github.com/erasmus-without-paper/ewp-specs-api-registry
[sec-v2]: https://github.com/erasmus-without-paper/ewp-specs-sec-intro/tree/stable-v2
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management#statuses
