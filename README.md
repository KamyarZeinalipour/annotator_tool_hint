# README

## Annotator Tool

This project is a **Python-based annotation tool** for processing datasets using a graphical user interface (GUI) powered by [Gradio](https://gradio.app/). The tool enables annotators to review, rate, and provide feedback on various fields in a dataset while automatically saving progress.

---

## Features

- **Interactive Annotation GUI**:
  - Displays dataset fields (`Text`, `Question`, `Answer`, etc.).
  - Collects ratings for hints and question classes using radio buttons.
  - Accepts comments for each entry.
- **Automatic Progress Saving**:
  - Annotations are stored in a CSV file with a timestamp and annotator details.
  - Automatically resumes from the last saved index.
- **Customizable Input Datasets**:
  - Handles input datasets with missing or empty fields by providing default values.

---

## Prerequisites

- Python 3.8 or higher
- Required Python libraries:
  - `os`
  - `time`
  - `pandas`
  - `gradio`
  - `fire`

Install dependencies using:
```bash
pip install pandas gradio fire
```

---

## Usage

### Command-Line Arguments
The script is executed with the following required arguments:

1. **`current_index`** *(Optional)*: Index to resume from. Default is `0`.
2. **`annotator_name`** *(Required)*: Name of the annotator for tracking progress.
3. **`examples_batch_folder`** *(Required)*: Path to the CSV file containing the dataset to annotate.

### Example
Run the script:
```bash
python annotator_tool.py main --current_index=0 --annotator_name="John Doe" --examples_batch_folder="data/sample_batch.csv"
```

### Inputs in Dataset File
The input dataset (`examples_batch_folder`) should be a CSV file with the following fields:
- `text`: The main text to annotate.
- `Question`: The related question.
- `Answer`: The corresponding answer.
- `Question Class`: The classification of the question.
- `hint_type`: The type of hint provided.
- `generated hint`: The hint text.

> **Note**: Missing fields are automatically filled with `[empty]`.

---

## GUI Overview

1. **Text and Fields**:
   - Displays the `text`, `Question`, `Answer`, and `Question Class`.

2. **Rating Options**:
   - **Hint Rating**:
     - **A**: Gold Standard.
     - **B**: Silver Standard.
     - **F**: Insufficient.
     - **Skipping**: Skip the current entry.
   - **Question Class Rating**:
     - **Acceptable**.
     - **Not Acceptable**.
     - **Skipping**.

3. **Comments**:
   - Provide any additional notes for the entry.

4. **Validation Button**:
   - Enabled only after selecting both ratings.

---

## Output

Annotated data is saved in a CSV file located in the `annotations` folder. The filename follows the format:
```
annotations_<dataset_filename>.csv
```

Each row in the output includes:
- Original dataset fields.
- Annotator name.
- Timestamp.
- Ratings (`Hint Rating`, `Question Class Rating`).
- Comments.

---

## Customization

### CSS Styling
The tool's appearance can be customized by modifying the `css` string in the code.

### Gradio Theme
The tool uses `gr.themes.Soft()` as the default theme. To use another theme, update the `Blocks` initialization.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE.text) file for details.

---

## Acknowledgments

Special thanks to the contributors and the open-source community for their valuable libraries and tools.
