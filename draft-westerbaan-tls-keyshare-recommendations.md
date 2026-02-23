---
title: "Updated recommendations for TLS keyshares"
category: standard

docname: draft-westerbaan-tls-keyshare-recommendations-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
v: 3
area: SE
workgroup: tls
keyword:

author:
 -
    fullname: Bas Westerbaan
    organization: Cloudflare
    email: bas@cloudflare.com

normative:

informative:

...

--- abstract

TODO Abstract


--- middle

# Introduction

TODO Introduction


# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

TODO Security


# IANA Considerations

This document updates the [TLS Supported Groups registry](https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-8), according to the procedures in {{Section 6 of RFC9847}} as follows.

| Value | Description        | Recommended |
|-------|--------------------|-------------|
| 23    | secp256r1          | N           |
| 24    | secp384r1          | N           |
| 29    | x25519             | N           |
| 30    | x448               | N           |
| 4588  | X25519MLKEM768     | Y           |
| 4589  | SecP384r1MLKEM1024 | Y           |

--- back
