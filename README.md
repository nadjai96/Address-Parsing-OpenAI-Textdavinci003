# Address Parser

This Jupyter notebook parses addresses from a given CSV file and extracts the street name, postcode, city, state, and country. The extracted information is saved back into new columns in the CSV file. 

## Requirements

This script requires the following Python libraries:

- pandas
- numpy
- tqdm
- chardet
- openai

You can install them using pip:

```bash
pip install pandas numpy tqdm chardet openai
In addition, you will need access to the OpenAI GPT-3 API, and your API key should be stored as an environment variable.

Setup
Install the required Python libraries:

pip install pandas numpy tqdm chardet openai
Set your OpenAI API key as an environment variable. Replace your-key-here with your actual key:

export OPENAI_KEY="your-key-here"
Run the Jupyter notebook:

jupyter notebook address_parser.ipynb
How It Works
The notebook reads a CSV file, loops over its rows, and sends prompts to the OpenAI API to extract the street, postcode, city, state, and country from each address. The results are saved into new columns in the dataframe. The updated dataframe is then saved to a new CSV file.

The script uses regular expressions to parse the response from the API and pandas to manage the data.

Example
Before running the script, your data may look something like this:

| Account_Name | Mailing_Address | Mailing_Street | Mailing_City | Mailing_State | Mailing_Zip | Mailing_Country |
| --- | --- | --- | --- | --- | --- | --- |
| Account1 | 123 Main St, Springfield, IL 12345, USA |  |  |  |  |  |
| Account2 | 456 Pine St, Metropolis, CA 54321, USA |  |  |  |  |  |

The 'Mailing_Street', 'Mailing_City', 'Mailing_State', 'Mailing_Zip', and 'Mailing_Country' columns are initially empty.

After running the script, the address data is parsed into separate columns:

| Account_Name | Mailing_Address | Mailing_Street | Mailing_City | Mailing_State | Mailing_Zip | Mailing_Country |
| --- | --- | --- | --- | --- | --- | --- |
| Account1 | 123 Main St, Springfield, IL 12345, USA | 123 Main St | Springfield | IL | 12345 | USA |
| Account2 | 456 Pine St, Metropolis, CA 54321, USA | 456 Pine St | Metropolis | CA | 54321 | USA |

Note
The script skips over rows if the address is missing or if the 'Account_Name' is the same as the previous row's 'Account_Name'.

In a Jupyter notebook, the functions would typically be defined in separate cells. Then the cells to load the data and apply the functions would be run in sequence.
