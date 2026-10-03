# Developer Cookbook — api-oss-embed
**Stack:** Python 3.11, sentence-transformers, torch, numpy, AIOSS_FORMAT
**Domain:** Sovereign embedding service: local vector computation for all Anticloud modules
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```python
from api_oss_embed import EmbeddingService
service = EmbeddingService(fast_model='all-MiniLM-L6-v2', accurate_model='./pax-27b-q4.gguf', aioss_chain='./embed.aioss')
vec = service.embed('AIOSS chain append operation', quality='fast')  # 384-dim
vec = service.embed('Detailed clinical analysis', quality='accurate')  # 4096-dim
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every api-oss-embed output:
chain_hash = aioss_append("./api_oss_embed.aioss",
                           result_bytes, "api-oss-embed")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-embed operations are logged to api-oss-logging and audited by api-oss-compliance.
