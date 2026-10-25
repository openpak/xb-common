# Notes: xb-common

Shared Go packages for the OpenPak original-Xbox services (`xb-account`,
`xb-auth`, `xb-gateway`, `xb-social`, `xb-enroll`, `xb-tou`). Module
`github.com/openpak/xb-common`. Only code imported by two or more services lives here; it holds no feature state and no runtime.

Single-service code stays in that service (`sgwire` in xb-gateway, `xbcodes` in xb-account).
