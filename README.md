<a href="https://gola.apimart.ai/k-IHJgxo"><img src="banner.jpg" alt="GPT Image 2.6" width="100%" /></a>

# GPT Image 2.6 API — endpoint, parameters and pricing

> How to call GPT Image 2.6 on APIMart: async task API, parameters, errors and cost.

[![Awesome](https://awesome.re/badge.svg)](https://github.com/sindresorhus/awesome) [![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](LICENSE)

**[👉 Try GPT Image 2.6 on APIMart](https://gola.apimart.ai/k-IHJgxo)**

`https://gola.apimart.ai/k-IHJgxo`

[💰 Pricing](https://gola.apimart.ai/k-79IoGo) · [🔑 Get an API key](https://gola.apimart.ai/k-oEb0Sj)

---

## Quick start

```bash
curl -X POST https://api.apimart.ai/v1/images/generations \
  -H "Authorization: Bearer $APIMART_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"gpt-image-2.6-flare","prompt":"a red apple on a white table","n":1,"size":"1024x1024"}'
```

The API is asynchronous: the call returns a `task_id`, then you poll it.

```bash
curl https://api.apimart.ai/v1/tasks/<task_id> -H "Authorization: Bearer $APIMART_API_KEY"
```

## Models

| Model id | Variant | Notes |
|---|---|---|
| `gpt-image-2-6` alias | — | resolves to Flare |
| `gpt-image-2.6-flare` | Flare | faster profile |
| `gpt-image-2.6-sunburst` | Sunburst | quality profile |

## Parameters

| Field | Type | Description |
|---|---|---|
| `model` | string | `gpt-image-2.6-flare` or `gpt-image-2.6-sunburst` |
| `prompt` | string | text prompt (English works best) |
| `n` | int | number of images, 1-4 |
| `size` | string | `1024x1024`, `1536x1024`, `1024x1536` |
| `reference_image` | url | optional image-to-image input |

## Response

```json
{"code":200,"data":[{"status":"submitted","task_id":"task_xxx"}]}
```

Poll `GET /v1/tasks/{task_id}`; on success `data.result.images[0].url` holds the image,
`data.cost` holds the **final** billed amount in USD.

## Pricing

| Variant | Price |
|---|---:|
| GPT Image 2.6 Flare | **$0.0198 / image** |
| GPT Image 2.6 Sunburst | **$0.0198 / image** |

Member discounts stack on top. See the pricing page for live numbers.

## Errors

| Code | Meaning |
|---|---|
| `model_not_found` | model id typo or not rolled out yet |
| `invalid_request_error` | bad parameter (e.g. unsupported size) |
| `task_failed` | upstream refused; check `error.message` |

---

## Related

- Prompt library: [gpt-image-2-6-prompts](https://github.com/fujc683/awesome-gpt-image-2-6-prompts)
- More image models: [awesome prompt collections](https://github.com/fujc683?tab=repositories)

## License

CC BY 4.0
