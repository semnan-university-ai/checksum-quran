```python
import sys, os, hashlib
from collections import OrderedDict as od
```


```python
def getHashSums(file_path):
    hashSums = od()
    hashSums['md5sum'] = hashlib.md5()
    hashSums['sha1sum'] = hashlib.sha1()
    hashSums['sha224sum'] = hashlib.sha224()
    hashSums['sha256sum'] = hashlib.sha256()
    hashSums['sha384sum'] = hashlib.sha384()
    hashSums['sha512sum'] = hashlib.sha512()

    with open(file_path, 'rb') as fd:
        dataChunk = fd.read(1024)
        while dataChunk:
            for hashsum in hashSums.keys():
                hashSums[hashsum].update(dataChunk)
            dataChunk = fd.read(1024)

    results = od()
    for key,value in hashSums.items():
        results[key] = value.hexdigest()         
    return results
```


```python
for key,value in getHashSums("data/clean.txt").items():
    print(key,value)
```

    md5sum 32c7dbed552db5fbc4a9c5383d05edf9
    sha1sum 259f672a325f34d522ec96c00327fed2a0f7555c
    sha224sum 9ad8a7917ff09339ec8184471455fedc5e3da6404967358f012a9532
    sha256sum 6f4502d7f85972495f343e88d7e6170ddaa7067224b44e5a1f356e75c7c2bb29
    sha384sum 6462f166dc15e35ece4591614b2591462b825f2fe368555bfd94001b614480bc8071fe3ae935ee1390108dddd1ffe9ed
    sha512sum 3d080a2206689fc725b3de14c95ea842604b402b161aa66e6c8b7f2fa3e303a90c968e75e71a5d223a97fc69705457d449ebf9545fd4a129af733250070d5ad8
    


```python
for key,value in getHashSums("data/quran.txt").items():
    print(key,value)
```

    md5sum 8feaa9648bf28e17ea9807fdf51097c3
    sha1sum 5e5d0dcd8e095430344e8dfb64658ae8e383de4e
    sha224sum bb8f5cff21cd70b54779522f6c1690ea989cb8be23f8f86ec890136c
    sha256sum fa5da3c473949f5f32db356613429d6a75717dee8ff49eb8f91b8b0194cd03ab
    sha384sum 504a2092ea6d9263f528e4b0b1e7156859ff0d0ddeb7f9b6ec6db369f6edca70235f460fec83a198eaae139f7930ac70
    sha512sum e5693d42800141d71fb4639d4076d66140c296683e99c90bf3abe35ba47c2a55bf5333f807d33a265479ba0bb463630e041999dbc32d57b9202601f8d1f6aaf3
    


```python
for key,value in getHashSums("data/uthmani.txt").items():
    print(key,value)
```

    md5sum c786f77394fcbbdbec9092a2e98a5d96
    sha1sum ade50b4e0c2869bcec891a366d4f405670a367f4
    sha224sum b219e003c1821df9941a40b2cc7bbc4d70bfdc04b397adc23ead4167
    sha256sum fe8fd2e0ae4fd4c2d53975e7fce4da96480c7347d872adeaf71d2aac37d5e5a2
    sha384sum 69e2570ac7f6ead5635b4cecb5bc998c5e998984babddb0cad035880129b80025fc71db5ef498201a248008033eadd08
    sha512sum 165385059d0897ad1e16fed1c1f3af097fbd7e7eb4e4a4e572f90f575bbad35fd250034212a58a71b32b58f666f1825853660e1bb4a0e8545258aa77ba33e16d
    


```python

```
