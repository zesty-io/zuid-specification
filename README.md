# ZUID Specification

* A ZUID is a string
* A ZUID is typically 15-20 characters in length, but may be up to 50 characters (a `VARCHAR(50)` in MySQL is recommended)
* A ZUID contains 3 components, separated by hyphens/dashes

Example ZUID:

```
1-1b123a2f0-qw2n4
```

## Component 1: Entity Prefix

The first component is a string that acts as a prefix, encoding that metadata.

* Component 1 is a hexadecimal string
* It is typically encoded from a prefix stored as an integer

These string prefixes are static and are provided in each library as some form of constant. Typically they are stored as integers and will need encoded as hex when generating an ID.

## Component 2: Time Encoded as a String

* This is encoded as hexidecimal like `a3f13d`
* We substract `1420070400` to shorten the hash slightly
    * `1420070400` is January 1st, 2015 (in seconds), before the first zuid was generated

Example:

```
Date (and time):
Wed Apr 12 2017 14:53:06 GMT-0700 (PDT)

In seconds:
1492033987

As hex:
"58eea1c3"
```

## Component 3: A Random Alphanumeric String

* This is a random alphanumeric string.
* It is by default generated as 5 characters long.
* It can be generated as up to 15 characters if more possibilities as desired
* It randomly selects from the characters `bcdfghjklmnpqrstvwxz0123456789`
* It does not use vowels to avoid forming words in IDs


# Libraries

* [zuid-js](https://github.com/zesty-io/zuid-specification)
* [zuid-php](https://github.com/zesty-io/zuid-php)
* [zuid-mysql](https://github.com/zesty-io/zuid-mysql)

# ZUID Entity Prefixes

Below as ZUID Entity Prefixes encoded as JSON. This document is the definitive source for these. All other libraries should conform to it.

```json
{
    "SITE": 0
}
```

