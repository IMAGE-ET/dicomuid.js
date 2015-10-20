# dicomuid.js
Generate DICOM UID values in Javascript

Another approach to generating UIDs that does not require obtaining one's own root prefix can take advantage of a standard prefix established for using a Universally Unique Identifier (UUID), which are used in many libraries and applications as identifiers for distributed objects. The procedure is described in ITU X.667 Information technology - Open Systems Interconnection - Procedures for the operation of OSI Registration Authorities: Generation and registration of Universally Unique Identifiers (UUIDs) and their use as ASN.1 Object Identifier components; in essence it involves converting the normal hyphenated hexadecimal string form of a UUID into a single large decimal number and appending it to the prefix "2.25.". E.g., the UUID "f81d4fae-7dec-11d0-a765-00a0c91e6bf6" becomes the DICOM UID (OID) "2.25.329800735698586629295641978511506172918". Since this process involves a very large number, it is most easily done with a language or library that supports unlimited length integers (e.g., java.math.BigInteger), and which provides tools to generate and parse UUIDs (e.g., java.util.UUID). Fortunately, the maximum size of the decimal integer to represent a UUID plus the prefix fits into the DICOM 64 character limit for UIDs. [More information here](http://www.dclunie.com/medical-image-faq/html/part2.html#UID)

## Getting Started

Install it in your browser:

```html
<script src="dicomuid.js"></script>
```

Usage:

```javascript
// Create new DICOM UID.
// Result will be like 2.25.176371623884904210764200284661930180516
var uid1 = DICOMUID.create();

// Create DICOM UID from a RFC4122 v4 UUID.
// Result for line below is 2.25.329800735698586629295641978511506172918
var uid2 = DICOMUID.create("f81d4fae-7dec-11d0-a765-00a0c91e6bf6");

```

## Depends on

[node-uuid](https://github.com/broofa/node-uuid),
[BigInteger](https://github.com/peterolson/BigInteger.js)

