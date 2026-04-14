---
title: "Updated recommendations for TLS keyshares"
category: std

docname: draft-westerbaan-tls-keyshare-recommendations-latest
updates: 8446, 9325
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
  RFC8446:
  RFC9325:
  RFC9847:

informative:
  RFC9794:
  I-D.ietf-pquip-pqc-engineers:

...

--- abstract


This document updates the TLS Supported Groups registry
(previously EC Named Curve Registry)
in the light
of the future arrival of cryptographically relevant quantum computers:
it sets the Recommended column of X25519MLKEM768 to Y,
and removes the Recommended status from non-post-quantum key shares.

[[ NOTE I use key share in the title and here as it's more accurate
   than "group" and perhaps more well known in the context TLS
   than key agreement or key exchange. ]]

--- middle

# Introduction

A future cryptographically relevant quantum computer (CRQC)
{{RFC9794}} can decrypt
TLS handshakes recorded today that do not use post-quantum algorithms
for their key shares:
algorithms designed to be resistant against quantum attack.
This threat is known as "harvest now, decrypt later" (HNDL)
{{I-D.ietf-pquip-pqc-engineers}}.

To address this threat, this document updates the
[TLS Supported Groups registry](https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-8)
as defined in {{Section 6 of RFC9847}}:
it marks X25519MLKEM768 as Recommended (Y),
as it is a post-quantum key share with widespread support,
and removes the Recommended status from non-post-quantum key shares
by setting them to N.


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

| Value | Description        | Recommended |
|-------|--------------------|-------------|
| 23    | secp256r1          | N           |
| 24    | secp384r1          | N           |
| 29    | x25519             | N           |
| 30    | x448               | N           |
| 4588  | X25519MLKEM768     | Y           |


--- back
