# ZUID Specification

Zesty Unique Identifiers (ZUID) '/zoo ids/' are used to label each Zesty.io created resource from content to users to media to content fields etc. everything has a ZUID. ZUID are used for data referencing in the user interfaces and rest APIs. ZUIDs are also bound to Audit Trail Logs in the system.

* A ZUID is a string
* A ZUID is typically 15-20 characters in length, but may be up to 50 characters
* A ZUID contains 3 components, separated by hyphens/dashes

Example ZUID:

```
structure: component1-component2-component3
lengths: maxlen5-maxlen10-maxlen35

e.g. 1-1b123a2f0-qw2n4
```

## Component 1: Entity Prefix

* Is an integer (ultimately stored as part of a string)
* Limited to 5 characters.

*These string integers are static representations of specific entity types and are provided in each library as some form of constant.*

## Component 2: Time Encoded as a String

* __Can NOT be seconds based measurement.__ This is not precise enough for unique hashes.
* Must be 10 characters
* Encoded as hexidecimal string like `d0f1b38ad3`

Example:

```
Date (and time):
2018-03-23 14:36:18.643025 -0700 PDT m=+0.000811554

In nano seconds:
1521840978643025000

As hex:
"d0f1b38ad3"
```

## Component 3: A Random Alphanumeric String

* This is a random alphanumeric string.
* Minimum of 6 character length.
* Maximum of 35 characters length.
* It randomly selects from the character set `bcdfghjklmnpqrstvwxz0123456789`
* It does not use vowels to avoid forming words in IDs


# Libraries

* [zuid-js](https://github.com/zesty-io/zuid-js)
* [zuid-php](https://github.com/zesty-io/zuid-php)
* [zuid-mysql](https://github.com/zesty-io/zuid-mysql)

# ZUID Entity Prefixes

See `prefixes.json` for ZUID Entity Prefixes encoded as JSON. This file is the definitive source for prefixes. All other libraries should conform to it.
