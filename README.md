# raven: A small Python library that calls local models cleanly, handles streaming, measures inference, and teaches you how HTTP clients work.
Start with this target:
```python
from local_llm_client import LocalLLM

client = LocalLLM(base_url="http://127.0.0.1:8001", model="qwen")

response = client.chat("Count from 1 to 10")
print(response.text)
print(response.metrics)
```
Then streaming:
```python
for chunk in client.stream("Count from 1 to 10"):
    print(chunk.text, chunk.kind, chunk.latency_ms)
```
Eventually:
```python
result = client.chat_json(
    prompt="Extract this receipt as JSON...",
    schema=ReceiptSchema,
)
```
