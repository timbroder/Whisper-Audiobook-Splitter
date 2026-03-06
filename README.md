# Whisper Audiobook Chapterizer

This script is designed to split an audiobook into chapters based on detected chapter headings in the audio. It uses the extremely fast `whisper.cpp` model for transcription and `ffmpeg` for audio processing on Apple silion.

![Project Logo](logo.jpg)

## Features

- Transcribes audio files to text using the `whisper.cpp` model (default `large-v3-turbo`)
- Detects chapter headings in the transcribed text.
- Splits the audio file into separate chapters.
- Generates output files including SRT, CUE, Markdown, and raw text with timestamps.

## System requirements
- Tested only on Mac os
- Procesor Apple silicon (M1/M2/M3)

## Requirements

- Python 3.x
- `ffmpeg`
- `mutagen`
- `pywhispercpp`

## Installation & usage

1. Clone the repository:
2. Create and activate a virtual environment:
   ```bash
   python -m venv .venv
   source .venv/bin/activate
   ```
3. Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```
4. Place your MP3 files in the `Input/` directory.
5. Run the script:
   ```bash
   python Splitter.py
   ```
## Customization

- **Skip Phrases**: You can customize the phrases to skip when detecting chapters by editing the `skip_phrases.json` file.

### Parameters

| Parameter | Default | Description |
|---|---|---|
| `-i`, `--input` | — | Path to a specific MP3 file to process |
| `--input_dir` | `Input` | Directory to search for MP3 files (used when `--input` is not provided) |
| `--output_dir` | `Output` | Directory to write output files to |
| `--model` | `base` | Whisper model to use for transcription |
| `--threads` | `6` | Number of threads to use for transcription |
| `--custom_chapter_phrase` | — | Custom regex phrase to use for chapter detection instead of the default "Chapter N" pattern |
| `--chapter_index` | `0` | Number at which chapter file names will start |
| `--no_intro` | — | Do not name the first output file "Intro" |

Example:
```bash
python Splitter.py --input_dir /path/to/audiobooks --output_dir /path/to/output --model large-v3-turbo
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [whisper.cpp](https://github.com/ggerganov/whisper.cpp) for the transcription model.
- [FFmpeg](https://ffmpeg.org/) for audio processing.