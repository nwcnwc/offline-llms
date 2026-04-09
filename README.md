# Offline LLMs — In-Browser AI Chat

Single HTML files that run LLMs entirely in your browser via WebGPU. No server, no API keys, no data leaves your machine.

## Models

### [gemma-4-e2b-offline.html](gemma-4-e2b-offline.html) — Google Gemma 4 E2B

- **Multimodal** — text, image, and audio input
- **Size**: ~3-4 GB download (q4f16 quantization), cached after first load
- **Context**: 128K tokens
- **Speed**: ~20-25 tok/s (M3 Mac), ~1.7 tok/s (integrated GPU)
- **Engine**: [@huggingface/transformers](https://huggingface.co/docs/transformers.js) + ONNX

### [ms-bitnet-offline.html](ms-bitnet-offline.html) — Microsoft BitNet b1.58 2B

- **Text only** — no image/audio support
- **Size**: ~500 MB download (native 1-bit weights), cached after first load
- **Context**: 4K tokens
- **Architecture**: 1.58-bit ternary weights {-1, 0, +1} — the smallest frontier-class model
- **Engine**: [wllama](https://github.com/ngxson/wllama) (llama.cpp compiled to WASM) — runs on CPU, no GPU needed
- **Custom build**: `wllama-bitnet/` contains a custom WASM build of llama.cpp with i2_s (BitNet ternary) support

## Usage

1. Open any `.html` file in **Chrome 113+** or **Edge 113+** (WebGPU required)
2. Wait for the model to download (cached for offline use after first load)
3. Start chatting

## Requirements

- Chrome 113+, Edge 113+, or Safari 18+ with WebGPU enabled
- A GPU with enough VRAM (~1.5-2 GB)

## License

MIT
