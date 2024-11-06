# Bases
Easy\
General Skills\
picoCTF 2019\
Author: Sanjay C/Danny T
#### Description
> What does this `bDNhcm5fdGgzX3IwcDM1` mean? I think it has something to do with bases.
## Solution
Use [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Base64('A-Za-z0-9%2B/%3D',true,false)) to make the conversion.
```
From_Base64('A-Za-z0-9+/=',true,false)
```
### Flag
`picoCTF{l3arn_th3_r0p35}`
