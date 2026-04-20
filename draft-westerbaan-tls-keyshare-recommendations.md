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
 -
    ins: M. Usama Sardar
    fullname: Muhammad Usama Sardar
    organization: TU Dresden
    email: muhammad_usama.sardar@tu-dresden.de

normative:
  RFC8446:
  RFC9325:
  RFC9847:

informative:
  RFC9794:
  I-D.ietf-pquip-pqc-engineers:

...

--- abstract


This document recommends X25519MLKEM768 for use in TLS
by updating its entry in the TLS Supported Groups registry
(previously EC Named Curve Registry)
to Recommended in the light
of the future arrival of cryptographically relevant quantum computers.

[[ NOTE We use key share in the title and here as it's more accurate
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
to mark X25519MLKEM768 as Recommended (Y)
as defined in {{Section 6 of RFC9847}},
as it is a post-quantum key share with widespread support.


# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

Before the arrival of a CRQC,
a TLS connection that negotiated a non-post quantum key share can be recorded
and decrypted in the future.

# IANA Considerations

This document updates the [TLS Supported Groups registry](https://www.iana.org/assignments/tls-parameters/tls-parameters.xhtml#tls-parameters-8), according to the procedures in {{Section 6 of RFC9847}} as follows.

| Value | Description        | Recommended |
|-------|--------------------|-------------|
| 4588  | X25519MLKEM768     | Y           |


--- back
