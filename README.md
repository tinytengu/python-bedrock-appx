# python-bedrock-appx

Small Python library for downloading `.appx` packages of Minecraft Bedrock (Windows)

## Usage example
### Get particular version
```python
from bedrock.versions import Versions

version = Versions.get_by_version("1.8.0.24")
print(version)
# Version(version='1.8.0.24', update_id='659F8B59-3FC7-4242-A06E-DA1AB4BDE3C4', is_beta=False, is_deprecated=False, uri='http://tlu.dl.delivery.mp.microsoft.com/filestreamingservice/files/f92d1fa4-c8a5-43dc-855b-187463e01010?P1=1633035160&P2=404&P3=2&P4=JCD0K3I65Aly%2fiyp325zPef6Iqn5xepGTtf1yIwCQklF0k9Y26l8iMfiZtRJIEqmC7rH0Q0zxiQFNu8vGTqp9A%3d%3d')
```

### Getting all the versions
```python
from bedrock.versions import Versions

for ver in Versions.get_all():
    if ver.is_beta:
        print(f"{ver.version} (Beta): Unable to get .appx URI.. for now.")
        continue
    
    if ver.is_deprecated:
        print(f"{ver.version} (Deprecated): Unable to get .appx URI, package is deprecated.")
        continue

    print(f"{ver.version}: {ver.uri}")

```