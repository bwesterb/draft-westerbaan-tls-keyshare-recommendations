---
title: "Updated recommendations for TLS keyshares"
category: std

docname: draft-westerbaan-tls-keyshare-recommendations-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
v: 3
area: "Security"
workgroup: "Transport Layer Security"
keyword:
venue:
  group: "Transport Layer Security"
  type: "Working Group"
  mail: "tls@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/tls/"
  github: "bwesterb/draft-westerbaan-tls-keyshare-recommendations"
  latest: "https://bwesterb.github.io/draft-westerbaan-tls-keyshare-recommendations/draft-westerbaan-tls-keyshare-recommendations.html"

author:
 -
    ins: B.E. Westerbaan
    fullname: Bas Westerbaan
    organization: Cloudflare
    email: bas@cloudflare.com

normative:

informative:
  RFC9847:
  RFC9794:
  I-D.ietf-pquip-pqc-engineers:

...

--- abstract


This document updates the recommendations for key shares algorithms (TLS
supported groups; previously EC Named Curve Registry) in the light
of the future arrival of cryptographically relevant quantum computers.

[[ NOTE I use key share in the title and here as it's more accurate
   than "group" and perhaps more well known in the context TLS
   than key agreement or key exchange. ]]

--- middle

# Introduction

A future cryptographically relevant quantum computer (CRQC)
{{RFC9794}} can decrypt
TLS handshakes recorded today that do not use post-quantum algorithms for their key shares:
algorithms designed to be resistant against quantum attack
This threat is known as "harvest now, decrypt later" (HNDL)
{{I-D.ietf-pquip-pqc-engineers}}.

RFC9847 defines the permitted value of the "Recommended" column
of the [TLS Supported Groups registry](https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-8) as:

Y:
: Indicates that the IETF has consensus that the
    item is RECOMMENDED. This only means that the associated
    mechanism is fit for the purpose for which it was defined.
    Careful reading of the documentation for the mechanism is
    necessary to understand the applicability of that mechanism.
    The IETF could recommend mechanisms that have limited
    applicability, but will provide applicability statements that
    describe any limitations of the mechanism or necessary constraints
    on its use.

N:
: Indicates that the item has not been evaluated by
    the IETF and that the IETF has made no statement about the
    suitability of the associated mechanism. This does not necessarily
    mean that the mechanism is flawed, only that no consensus exists.
    The IETF might have consensus to leave an items marked as "N" on
    the basis of its having limited applicability or usage constraints.

D:
: Indicates that the item is discouraged. This marking could be used to identify
    mechanisms that might result in problems if they are used, such as
    a weak cryptographic algorithm or a mechanism that might cause
    interoperability problems in deployment. When marking a registry entry as
    “D”, either the References or the Comments Column MUST include sufficient
    information to determine why the marking has been applied. Implementers and
    users SHOULD consult the linked references associated with the item to
    determine the conditions under which the item SHOULD NOT or MUST NOT be used.

Given the HNDL threat, the IETF cannot recommend key shares for general use
that do not offer post-quantum resistance, and this document updates
the [TLS Supported Groups registry](https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-8)
accordingly.

Among the currently registered post-quantum key share algorithms, IETF
recommends X25519MLKEM768 for its widespread support.


# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

Before the arrival of a cryptographically relevant quantum computer (CRQC),
a TLS connection that negotiated a non-post quantum key share can be recorded
decrypted in the future.

After the arrival of a CRQC, allowing a non-post quantum key share to be
negotiated allows for an active quantum attack that achieves MITM,
even if the server certificate is post quantum.

# IANA Considerations

This document updates the [TLS Supported Groups registry](https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-8), according to the procedures in {{Section 6 of RFC9847}} as follows.

## Recommend

| Value | Description        | Recommended |
|-------|--------------------|-------------|
| 4588  | X25519MLKEM768     | Y           |

## Discourage

| Value | Description        | Recommended | Comment
|-------|--------------------|-------------|-----------------------------------------------------------------------------|
| 9     | sect283k1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 10    | sect283r1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 11    | sect409k1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 12    | sect409r1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 13    | sect571k1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 14    | sect571r1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 22    | secp256k1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 23    | secp256r1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 24    | secp384r1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 25    | secp521r1          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 26    | brainpoolP256r1    | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 27    | brainpoolP384r1    | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 28    | brainpoolP512r1    | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 29    | x25519             | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 30    | x448               | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 31    | brainpoolP256r1tls13 | D         | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 32    | brainpoolP384r1tls13 | D         | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 33    | brainpoolP512r1tls13 | D         | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 34    | GC256A             | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 35    | GC256B             | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 36    | GC256C             | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 37    | GC256D             | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 38    | GC512A             | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 39    | GC512B             | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 40    | GC512C             | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 41    | curveSM2           | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 256   | ffdhe2048          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 257   | ffdhe3072          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 258   | ffdhe4096          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 259   | ffdhe6144          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |
| 260   | ffdhe8192          | D           | Vulnerable to store-now/decrypt-later quantum attack, see TBA:this-document |


--- back
