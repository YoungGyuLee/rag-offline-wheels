# rag-offline-wheels

Offline pip wheels for a simple local RAG (`sentence-transformers` + CPU `torch`).
All files are unmodified wheels from PyPI and download.pytorch.org.

| Release | Target | Contents |
|---|---|---|
| `v1` | Linux x86_64, Python 3.12 | `torch` 2.15.0+cpu, `sentence-transformers` 6.3.0, `transformers` 5.24.0, `numpy` 2.5.5 and dependencies (48 wheels) |

## Install

```sh
curl -fLO https://github.com/YoungGyuLee/rag-offline-wheels/releases/download/v1/rag-wheels-py312.tar
curl -fLO https://github.com/YoungGyuLee/rag-offline-wheels/releases/download/v1/SHA256SUMS
sha256sum -c SHA256SUMS
tar -xf rag-wheels-py312.tar
python3 -m venv .venv
.venv/bin/pip install --no-index --find-links rag-wheels-py312 "torch>=2.6" sentence-transformers numpy
```

## Without pip

If `python3 -m venv` fails (`ensurepip is not available`) or pip is missing, use the pip wheel in this repo.
A wheel can run pip directly without unpacking.

```sh
curl -fLO https://github.com/YoungGyuLee/rag-offline-wheels/raw/main/pip-26.3-py3-none-any.whl
echo "f3b60b20ffaadd4415ed7957212a38ac63fa4c5fa375bd0f4a797777940fad13  pip-26.3-py3-none-any.whl" | sha256sum -c
python3 -m venv --without-pip .venv
.venv/bin/python pip-26.3-py3-none-any.whl/pip install --no-index pip-26.3-py3-none-any.whl
.venv/bin/pip install --no-index --find-links rag-wheels-py312 "torch>=2.6" sentence-transformers numpy
```

Each package keeps its own license (see the wheel metadata).
