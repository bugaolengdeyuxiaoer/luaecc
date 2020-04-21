[lua-releases]: http://www.lua.org/download.html
[lua]: http://www.lua.org
# LuaECC

luaecc is the lua verion of easy ecc,but only support secp256k1.

some operations are accquired to make calculate faster,and you can find some numbers are coded in functions.

luaecc implement basic generate key pair, sign and verify ,that satisfy basic develop. 

## Prerequisites


- **[lua][]**: any one of the **latest major** [lua-releases].



Installation
---


- install luarocks 
  ```
    https://luarocks.org/#quick-start
  ```
- install bits with luarocks
  ```lua
    luarocks install luabitop
  ```
  

Generate private key  pub key pair
-- 
```lua
ecc_make_key(pubkey,privkey)
```


Sign 
---
```lua
ecdsa_sign(p_publicKey, p_hash, p_signature)
```

Verify 
---
```lua
ecdsa_verify(p_publicKey, p_hash, p_signature)
```


Demo
---
```lua
  
    local pub = {}
    local priv = {}
    local signature = {}
    ecc_make_key(pub,priv)
    print()
    local hash = {}
    
    -- just for test . this means "test"*8
    --for i = 1 ,8 do
    --    hash[(i-1)*4+1]= 116
    --    hash[(i-1)*4+2]= 101
    --    hash[(i-1)*4+3]= 115
    --    hash[(i-1)*4+4]= 116
    --end
    hash = str2bytes("testtesttesttesttesttesttesttest")
    print(bytes2hex(priv))
    print(bytes2hex(pub))
    ecdsa_sign(priv,hash,signature)
    local sigstr = ""
    
    for i = 1,64 do
        sigstr = sigstr ..string.format("%x",signature[i]/16)
        sigstr = sigstr ..string.format("%x",signature[i]%16)
    end
    print("signature ",string.lower(sigstr))
    print(ecdsa_verify(pub,hash,signature))
```
