# jsonl-runner

Feed a thousand prompts, get a thousand answers

## What it does

- Per-row overrides for model, system, temperature and max_tokens
- Idempotent: ids already in the output are skipped on a rerun
- 4xx fails fast; 429 and 5xx retry with jittered backoff
- JSONL in, JSONL out: the input is streamed line by line
- A bad input line is logged and skipped, never fatal
- Real rate limiting: sliding windows on requests/min and tokens/min
- Failures go to a sidecar file with error type, message and status
- Progress, token counts and a cost estimate on stderr

## How to use

```bash
python batch.py prompts.jsonl -o answers.jsonl --workers 4 --rpm 300
```

## Install

```bash
pip install -r requirements.txt
export OPENAI_API_KEY=sk-...
```

## Project structure

```text
├── .github/
│   └── workflows/
│       └── ci.yml
├── docs/
│   ├── faq.md
│   ├── tradeoffs.md
│   └── usage.md
├── examples/
│   └── quickstart.md
├── tests/
│   └── test_smoke.py
├── .editorconfig
├── .gitignore
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
├── SECURITY.md
├── batch.py
├── prompts.sample.jsonl
└── requirements.txt
```

## License

MIT. Do whatever you want.
