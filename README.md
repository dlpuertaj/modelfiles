# Ollama Custom Models

A collection of Ollama Modelfiles for specialized local AI assistants. Each model is tuned with a focused system prompt and optimized inference parameters for its specific use case.

## Models

### ModelfileCoding — General Coding Assistant

**Base model:** `qwen3.5:4b`

A general-purpose programming assistant focused on writing functional, secure, and efficient code across any language. Keeps temperature low (0.1) for deterministic output and uses a 32K context window.

**Best for:** Quick code generation, debugging, language-agnostic tasks, security reviews.

```sh
ollama create coding -f ModelfileCoding
ollama run coding
```

---

### ModelfileFlutter — Flutter/Dart Coding Companion

**Base model:** `qwen2.5-coder:7b`

A deep-specialist assistant for Flutter and Android development. Enforces Clean Architecture, SOLID principles, Effective Dart style, and opinionated patterns for state management (Riverpod/Bloc), routing (go_router), and error handling (`Either`/sealed types).

**Best for:** Feature development, widget refactoring, architecture decisions, code reviews, testing strategy.

```sh
ollama create flutter -f ModelfileFlutter
ollama run flutter
```

> **Low VRAM?** Change the first line to `FROM qwen3.5:4b` as a fallback.

---

### ModelfileKB — Personal Knowledge Base Agent

**Base model:** `qwen2.5:7b`

An autonomous agent that reads and writes Markdown notes to maintain a personal wiki. Follows a strict flat-file format with `[[wikilinks]]`, kebab-case filenames, and one-concept-per-note rules. Supports three workflows: **Ingest**, **Query**, and **Update**.

**Wiki location:** `C:\Users\dlpuerta\Dropbox\AREAS\NOTES\BRAIN\wiki\`

**Best for:** Processing raw notes, answering questions from your knowledge base, keeping the wiki up to date.

```sh
ollama create kb -f ModelfileKB
ollama run kb
```

---

## Quick Reference

| Model | File | Base Model | Context | Temp | Use Case |
|-------|------|------------|---------|------|----------|
| `coding` | ModelfileCoding | qwen3.5:4b | 32 718 | 0.1 | General coding |
| `flutter` | ModelfileFlutter | qwen2.5-coder:7b | 16 384 | 0.1 | Flutter / Android |
| `kb` | ModelfileKB | qwen2.5:7b | 32 768 | 0.3 | Knowledge base agent |

## Prerequisites

- [Ollama](https://ollama.com) installed and running locally.
- The base models pulled before creating a custom model:

```sh
ollama pull qwen3.5:4b
ollama pull qwen2.5-coder:7b
ollama pull qwen2.5:7b
```

## Creating / Updating a Model

```sh
# Create or recreate after editing a Modelfile
ollama create <name> -f <Modelfile>

# List your local models
ollama list

# Remove a model
ollama rm <name>
```
