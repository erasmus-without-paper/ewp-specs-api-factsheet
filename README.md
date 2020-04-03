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


### `hei_id` (required)

An identifier of the institution the client wants to retrieve information on.

Clients may retrieve proper HEI identifiers from other EWP APIs (most often,
the [Registry Service][registry-spec]). Servers MUST be able to accept all HEI
IDs declared in their [manifest files][discovery-api].


Security
--------

This version of this API uses [standard EWP Authentication and Security, Version 2][sec-v2].
Server implementers choose which security methods they support by declaring them in their Manifest API entry.

[develhub]: http://developers.erasmuswithoutpaper.eu/
[discovery-api]: https://github.com/erasmus-without-paper/ewp-specs-api-discovery
[registry-spec]: https://github.com/erasmus-without-paper/ewp-specs-api-registry
[sec-v2]: https://github.com/erasmus-without-paper/ewp-specs-sec-intro/tree/stable-v2
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management#statuses