# The Noetic API

Call Noetic from your own programs. It speaks the chat format most tools and libraries already use, so in most
cases you change two things: the base address and the key.

| | |
|---|---|
| Base address | `https://noetic.lol/v1` |
| Model | `noetic-0.1` |
| Sign requests with | `Authorization: Bearer nk_…` |
| Limits | 40 calls a minute for each key. Each call is one request on your plan |

## 1. Make a key

Sign in at [noetic.lol](https://noetic.lol) → **user menu → Sign-in and security → API keys → Make a key**. The key
is shown once. Noetic keeps only a fingerprint of it, so if you lose it, remove it and make another. An account can
hold five.

Keep keys on your server. Do not put one in a web page, a mobile app or a public repository.

## 2. Ask something

```bash
curl https://noetic.lol/v1/chat/completions \
  -H "Authorization: Bearer $NOETIC_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "noetic-0.1",
    "messages": [
      {"role": "system", "content": "You answer in one short paragraph."},
      {"role": "user", "content": "What is a closure?"}
    ]
  }'
```

```json
{
  "id": "chatcmpl-3f9a…",
  "object": "chat.completion",
  "model": "noetic-0.1",
  "choices": [{ "index": 0, "message": { "role": "assistant", "content": "A closure is…" }, "finish_reason": "stop" }],
  "usage": { "prompt_tokens": 31, "completion_tokens": 64, "total_tokens": 95 }
}
```

### Python

```python
import os
from openai import OpenAI

client = OpenAI(base_url="https://noetic.lol/v1", api_key=os.environ["NOETIC_KEY"])
reply = client.chat.completions.create(
    model="noetic-0.1",
    messages=[{"role": "user", "content": "Write a haiku about a build that passes."}],
)
print(reply.choices[0].message.content)
```

### JavaScript

```js
const res = await fetch('https://noetic.lol/v1/chat/completions', {
  method: 'POST',
  headers: { Authorization: 'Bearer ' + process.env.NOETIC_KEY, 'Content-Type': 'application/json' },
  body: JSON.stringify({ model: 'noetic-0.1', messages: [{ role: 'user', content: 'Name three sorting algorithms.' }] }),
});
const { choices } = await res.json();
console.log(choices[0].message.content);
```

## 3. Stream the answer

Send `"stream": true` and read server-sent events. Each event carries a piece of the answer in
`choices[0].delta.content`; the last one has `finish_reason`, and the stream ends with `data: [DONE]`.

```js
const res = await fetch('https://noetic.lol/v1/chat/completions', {
  method: 'POST',
  headers: { Authorization: 'Bearer ' + process.env.NOETIC_KEY, 'Content-Type': 'application/json' },
  body: JSON.stringify({ model: 'noetic-0.1', stream: true, messages: [{ role: 'user', content: 'Explain DNS in five sentences.' }] }),
});
for await (const part of res.body.pipeThrough(new TextDecoderStream())) {
  for (const line of part.split('\n')) {
    if (!line.startsWith('data: ') || line === 'data: [DONE]') continue;
    process.stdout.write(JSON.parse(line.slice(6)).choices[0].delta.content || '');
  }
}
```

## Reference

### `GET /v1/models`

Lists what the key can call. Today that is one model, `noetic-0.1`.

### `POST /v1/chat/completions`

| Field | | |
|---|---|---|
| `messages` | required | A list of `{role, content}`. Roles: `system`, `user`, `assistant`. Content is text, or a list of `{type: "text", text}` parts |
| `model` | optional | `noetic-0.1`. Any other name is refused |
| `stream` | optional | `true` for server-sent events |
| `temperature` | optional | 0 to 1.5. Default 0.4 |
| `max_tokens` | optional | Up to 16,000 |

### Errors

Errors come back as `{"error": {"message": "…", "type": "…"}}` with a sentence a person can read.

| Status | Type | Meaning |
|---|---|---|
| 400 | `invalid_request_error` | The body is not JSON, or has no message from the user |
| 400 | `content_policy` | The request is something Noetic never does. See below |
| 401 | `invalid_api_key` | The key is missing, mistyped or removed |
| 404 | `model_not_found` | A model other than `noetic-0.1` was asked for |
| 429 | `rate_limit_exceeded` | More than 40 calls in a minute with one key |
| 429 | `insufficient_quota` | Today's requests on your plan are used, or there is no credit left |
| 503 | `server_error` | Noetic could not answer just now. Try again |

## What a call costs

A call is one request on your account's plan, the same as asking in the app: it counts toward the daily limit, and
on a paid plan it uses credit by how much work it took. See [PRICING.md](PRICING.md). There is no separate API price.

## What the API does not do yet

- **Builds.** Asking the app to build a project runs many steps and writes files; over the API you get an answer to
  a conversation, not a project.
- **Pictures and files.** Text in, text out.
- **Tool calling.** Not yet.

If one of these is what you need, tell us at support@snns.dev: it decides what is built next.

## Limits that never move

The same fixed limits apply over the API as in the app, whatever your system message says: nothing sexual involving
anyone under 18, no help with weapons capable of mass casualties, no attacks on systems you do not own, no
harassment of real people. The full list is in the [acceptable-use rules](https://github.com/loverhaterlmao/snns-suite/blob/main/LEGAL.md#2-acceptable-use).

## Without a key

Two endpoints take no key and exist for the forms on the site: `POST /apply` (ask for an invitation) and
`POST /contact` (write to support). Both take JSON, are limited to a few an hour for each address, and answer
`{"ok": true}` or `{"error": "…"}`.
