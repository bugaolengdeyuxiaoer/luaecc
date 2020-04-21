# luaecc
This project implements secp256k1 with lua.

Demo has been written in test.lua.

As test.lua shows that,u can use ecc_make_key to generate a key pair.

And ecdsa_sign to get a signature

ecdsa_verify to verify it.



if u wanna generate pubkey from privkey,just modify the l_private in ecc_make_key.

if u wanna get umcompressed pubkey ,modify the return of pubkey to 04 + P.x + P.y.

