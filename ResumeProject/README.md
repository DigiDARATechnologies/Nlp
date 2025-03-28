# Extract Email using Regex

## Overview
This Python script extracts an email address from a given text string using **Regular Expressions (Regex)**. It identifies email patterns and returns the first matched email found. If no email is found, it returns `"Not Found"`.

## Features
- Uses regex to detect email addresses.
- Returns the first email found in the text.
- Handles various email formats including subdomains.

## Prerequisites
Ensure you have Python installed on your system. This script uses the `re` module, which is built into Python.

## Installation
Clone this repository and navigate to the project directory:

```sh
git clone https://github.com/yourusername/extract-email.git
cd extract-email
```

## Usage
### Example Code
```python
import re

def extract_email(text):
    """Extract email using regex."""
    email_match = re.search(r'[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+', text)
    print(email_match)  # Prints the match object
    print(email_match.group(0))  # Prints the extracted email
    return email_match.group(0) if email_match else "Not Found"

# Example Usage
text = "Please contact me at john.doe@example.com for details."
print(extract_email(text))
```

### Expected Output
```
<re.Match object; span=(20, 42), match='john.doe@example.com'>
john.doe@example.com
john.doe@example.com
```

If no email is found, it prints:
```
None
Not Found
```

## How It Works
1. The function `extract_email(text)` takes a text string as input.
2. It uses the regex pattern `[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+` to search for an email address.
3. If an email is found, it prints and returns the email.
4. If no email is found, it returns `"Not Found"`.

## Regex Breakdown
| Pattern | Explanation |
|---------|------------|
| `[a-zA-Z0-9_.+-]+` | Matches the username part of the email. |
| `@` | Matches the `@` symbol. |
| `[a-zA-Z0-9-]+` | Matches the domain name. |
| `\.` | Matches the dot before the domain extension. |
| `[a-zA-Z0-9-.]+` | Matches the domain extension (e.g., `.com`, `.org`). |

## Contributing
Feel free to fork this repository and improve the script. Pull requests are welcome!

## License
This project is licensed under the MIT License.


