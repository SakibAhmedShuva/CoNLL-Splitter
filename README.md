# CoNLL-Splitter

CoNLL-Splitter is a Python tool designed to split CoNLL (Conference on Natural Language Learning) formatted files into training, validation, and testing sets. This tool is particularly useful for researchers and practitioners working with NLP tasks that use CoNLL-formatted data.

## Features

- Split CoNLL files into training, validation, and testing sets
- Customizable split ratios
- Option to create only training and validation sets (no testing set)
- Preserves the `-DOCSTART-` / `-DOCSTART- -X- O` / `-DOCSTART- -X- O O` line (if present) in all output files
- Maintains the original format, including empty lines indicating new sentences
- Supports direct input of CoNLL files

## Installation

Clone this repository to your local machine:

```
git clone https://github.com/SakibAhmedShuva/CoNLL-Splitter.git
cd CoNLL-Splitter
```

## Requirements

- Python 3.6+
- No external dependencies required

## Usage

```python
from conll_splitter import split_conll

# Example usage
conll_file = "path/to/your/input.conll"
output_dir = "path/to/output/directory"

# Split into train (80%), validation (10%), and test (10%)
split_conll(conll_file, output_dir, ratio=(0.8, 0.1, 0.1))

# Split into only train (80%) and validation (20%)
split_conll(conll_file, output_dir, ratio=(0.8, 0.2, 0.0))
```

## Function Parameters

- `conll_file` (str): Path to the input CoNLL file
- `output_dir` (str): Directory where the split files will be saved
- `ratio` (Tuple[float, float, float]): Ratio for train, validation, and test splits. Default is (0.8, 0.1, 0.1)

## Output

The script will create up to three files in the specified output directory:

- `train.conll`: Training data
- `dev.conll`: Validation data
- `test.conll`: Test data (if the ratio for test set is > 0)

Each file will maintain the original CoNLL format, including the `-DOCSTART-` / `-DOCSTART- -X- O` / `-DOCSTART- -X- O O` line (if present in the original file) and empty lines indicating new sentences.

## Notes

- The script checks for the presence of a `-DOCSTART-` line at the beginning of the input file. If found, this line is preserved in all output files.
- The script ensures that the sum of the provided ratios does not exceed 1.0.
- If a ratio of 0 is provided for any split, that file will not be created.
- The data is shuffled before splitting to ensure randomness in the distribution.

## Contributing

Contributions to improve CoNLL-Splitter are welcome. Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
