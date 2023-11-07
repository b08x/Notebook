---
---


```
1. @Benchmarks can we downgrade the `httpx` dependency in `agbenchmark` to `^0.24.0`? I'm getting dependency resolution clashes in the agent now.
    
    `Because no versions of openapi-python-client match >0.14.0,<0.14.1 || >0.14.1,<0.15.0  and openapi-python-client (0.14.0) depends on httpx (>=0.15.4,<0.25.0), openapi-python-client (>=0.14.0,<0.14.1 || >0.14.1,<0.15.0) requires httpx (>=0.15.4,<0.25.0). And because openapi-python-client (0.14.1) depends on httpx (>=0.15.4,<0.25.0)  and agbenchmark (0.0.10) @ file:///home/reinier/code/agpt/Auto-GPT/benchmark depends on httpx (^0.25.0), agbenchmark (0.0.10) @ file:///home/reinier/code/agpt/Auto-GPT/benchmark is incompatible with openapi-python-client (>=0.14.0,<0.15.0). So, because agpt depends on both openapi-python-client (^0.14.0) and agbenchmark (0.0.10) @ file:///home/reinier/code/agpt/Auto-GPT/benchmark, version solving failed`
    
    (edited)
    
2. _[_5:54 PM_]_
    
    I can't upgrade `openapi-python-client` to `0.15.0` either because that requires Pydantic v2
```