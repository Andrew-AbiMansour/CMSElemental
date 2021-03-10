# Base Model
```python
from cmselemental.models import ProtoModel

class Model(ProtoModel):
    ...

stringified = Model.json()
data = Model.dict()
```

# Serialization/deserialization
```python
from cmselemental.util import serialize, deserialize

stringified = serialize(data, encodding="json", indent=4)
data = deserialize(stringified, encoding="json")
```

# Program execution
```python
from cmselemental.util.common import execute, temporary_directory
from cmselemental.util.importing import which

with temporary_directory(parent=parent, suffix="_psi_scratch") as tmpdir:
 
    success, output = execute(
        [which("psi4"), "--scratch", tmpdir, "--json", "data.json"],
        {"data.json": json.dumps(input_data)},
        ["data.json"],
        scratch_directory=tmpdir,
    )
```
