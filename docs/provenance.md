# Provenance

AGPL-3.0-only, see `LICENSE` and `NOTICE`. Derived from the Xombie project in part; the legacy Rust workspace remains in https://github.com/openpak/xbox-live.

Ported from Xombie (libs/xblive): `xbcrypto` (RC4/HMAC primitives) and `krb` (Kerberos structures, key derivation, public Xombie prototype keys kept as a denylist, `krb/keys.go`). Written for OpenPak, no Xombie code: `xbaccountapi`, `xbenrolapi`, `xbfeature`, `ratelimit`. Split from openpak/xbox-live at commit 7fc575dd21485791ed80149deba4f158e66044ae.
