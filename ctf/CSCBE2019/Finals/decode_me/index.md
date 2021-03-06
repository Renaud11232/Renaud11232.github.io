# Decode me

### [-$ cd ..](../)

Author: [alect096](https://alect096.github.io/CTFs/CSCBE2019/pre-finals_friday/friday_afternoon/decode_me/)

> We found this weird file on the workstation of one of our employees.. Are you able to decode it?
> +3D+30+33+53+7A+38+43+58+78+41+6A+65+72+59+30+63+78+49+55+62+61+70+33+4D+71+70+55+64+61+31+43
> +62+32+49+30+4D+78+4D+48+4E+50+70+30+49+32+55+58+4D+72+42+6A+53+7A+73+32+65+5A+70+6C+53

We firstly removed the `+` in this string. We obtained a hexadecimal string


```python
a = "3D3033537A38435878416A6572593063784955626170334D71705564613143623249304D784D484E507030493255584D72426A537A7332655A706C53"
a.decode("hex")
  =03Sz8CXxAjerY0cxIUbap3MqpUda1Cb2I0MxMHNPp0I2UXMrBjSzs2eZplS
```

We remarked that the obtained string was a reversed base64 encoded string.

We reversed it to get a correct base64 string.

```python
 _[::-1]
	SlpZe2szSjBrMXU2I0pPNHMxM0I2bC1adUpqM3pabUIxc0YrejAxXC8zS30=
```

After that, we decoded the base64 string to get the following result:

```python
import base64
base64.b64decode("SlpZe2szSjBrMXU2I0pPNHMxM0I2bC1adUpqM3pabUIxc0YrejAxXC8zS30=")
  'JZY{k3J0k1u6#JO4s13B6l-ZuJj3zZmB1sF+z01\\/3K}'
```

We remarked that the output has the same pattern then the flag of the competition: CSR{some_string}.

We tried thanks to this [website](https://cryptii.com/pipes/caesar-cipher) to check each shift to break the cesar cipher.
Here is the result and the `csr{d3c0d1n6#ch4l13u6e-sncc3ssfu1ly+s01\\/3d}`.

![shift and result](assets/result.png)
