API Documentation:
---------------------------------

Contents
--------

  * [Overview](#overview)
  * [API](#api)
  * [Resource URL](#resource-url)
  * [Example](#example)
  * [Best Practices](#best-practices)

Overview
--------

  JavaScript plugin for configuring and loading pixels. Provides an API for passing contact data to these pixels.

API
---

  The plugin is initialized with a [contact](#contact) object, and exposes no other methods.

###Methods

####init

Initializes the container on your page, loading 3rd party pixels.

**Parameters:**

[contact](#contact) object

e.g. `OurCompanyName.init({contact});`

###Contact

  A contact is written as a [Javascript Object Literal](http://www.dyn-web.com/tutorials/object-literal/) and may contain any of the following fields:

  | Parameter   | Description | Optional |
  |-------------|-------------|
  | `email`     | Email address. This is the only required field. | No |
  | `first`     | First name | Yes |
  | `last`      | Last name | Yes |
  | `phone`     | Free-form phone number | Yes |
  | `street1`    | The first line of the street address (e.g., `"123 Main St."`) | Yes |
  | `street2`   | Second line of the stree address (e.g., `"Apartment 1A"`)        | Yes |
  | `city`      | The city name  | Yes |
  | `state`     | The full U.S. state name or two-letter abbreviation | Yes |
  | `zip`       | The U.S. zip code, 5 or 9 letters, with or without hyphen | Yes |

  To set, pass a contact object to the init function:

  ```
  OurCompanyName.init({
    email:    "john.doe@domain.com",
    first:    "John",
    last:     "Doe",
    phone:    "123-456-6789",
    street1:   "123 Main St.",
    street2:  "Apartment 1A",
    city:     "Springfield",
    state:    "IL",
    zip:      "1234"
  });
  ```

Resource URL
------------

  Our script is loaded from the following URL:

  `/pixel/{version}/{clientId}/plugin.js`

  | Parameter | Description |
  |-----------|-------------|
  | `{version}` | Version of the plugin you wish to load.  Currently only `v1`
  | `{clientId}` | Your 36-character long unique client ID (includes letters, numbers, and hyphens. |

  e.g. `https://domain.com/pixel/v1/2ef0361b-e44b-49ec-9509-45c3c57e96b4/plugin.js`



Example
-------

  Include our tag, and initialize with your client data

  ```
  <script src="resourceURL" type="text/javascript"><script/>
  <script type="text/javascript">
  OurCompanyName.init({
       "email":"jdoe@domain.com",
       "first": "John",
       "last": "Doe",
       "state":"CO"
     });
  </script>
  ```

Best Practices
--------------

  This snippet should always be loaded in the page body rather than head. For optimal page load, place script tag at bottom of page HTML.
