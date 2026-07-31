# Voice-to-Study-Notes Pipeline

Convert raw voice recordings into structured study notes and flashcards — fully offline, using open-source models.

## What it does

This project takes an audio recording (e.g. a voice memo of a lecture or personal notes) and automatically:
1. **Transcribes** the audio to text using OpenAI's Whisper
2. **Splits** the transcript into logical topics using Llama 3 (run locally via Ollama)
3. **Summarizes** each topic into clean bullet points
4. **Generates flashcards** (Q/A format) from the summarized content
5. **Saves** the final study notes + flashcards to a single `.txt` file

The goal: turn messy spoken notes into exam-ready material with zero manual typing.

## Tech Stack

- **Speech-to-Text:** [OpenAI Whisper](https://github.com/openai/whisper) (base model)
- **LLM:** Llama 3 / Llama 3.2, served locally via [Ollama](https://ollama.com)
- **Orchestration:** LangChain (`langchain-core`, `langchain-ollama`, `langchain-text-splitters`)
- **Environment:** Google Colab (Python 3)

## How it works (pipeline)
Audio file (.wav) → Whisper transcription (.txt / .srt with timestamps) → LangChain text splitting into topics → Llama3 summarization per topic → Llama3 flashcard generation → Combined output saved to Complete_Study_Packet.txt

## Setup (Colab)

1. Install dependencies:
```bash
   pip install git+https://github.com/openai/whisper.git
   sudo apt install ffmpeg
   pip install langchain-text-splitters langchain-ollama langchain-core
   curl -fsSL https://ollama.com/install.sh | sh
```
2. Pull the Llama3 model:
```bash
   ollama pull llama3.2
```
3. Upload your audio file, update the `audio_file_path` variable, and run cells in order.

## Author

Built by Sofia , for capstone project for IBM SkillsBuild 6-Week Internship Program Jan 2026 , delivered by Edunet foundation.
