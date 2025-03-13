# Galaxy Tool Lookup Utility

## Description
This project provides a lookup function for an AI agent to interact with Galaxy tools. It retrieves a list of available tools along with partial XML metadata from their source code. The AI agent will later use this tool to determine available functionalities within the Galaxy platform and facilitate seamless integration of different tools. This lookup function serves as a foundational component, enabling the AI agent to make informed decisions about tool selection and usage.

The implementation utilizes `bioblend`, a Python library for interacting with Galaxy APIs, to fetch tool information and configurations programmatically.

## Prerequisites
Ensure you have Python installed along with the required dependencies.

## Installation
To install the required dependency, run:
```bash
pip install bioblend
```

## Usage
1. Import the necessary modules and authenticate with a Galaxy instance:
```python
from bioblend import galaxy

gi = galaxy.GalaxyInstance(url='https://usegalaxy.org/', key='API_KEY')
```
Replace `API_KEY` with your actual Galaxy API key.

2. Fetch available histories:
```python
hl = gi.histories.get_histories()
```

3. Access Galaxy configuration details:
```python
con = galaxy.config.ConfigClient(gi)
```

4. Retrieve a list of available tools:
```python
tools = gi.tools.get_tools()
```

5. Extract relevant XML metadata from tools:
```python
for tool in tools:
    tool_details = gi.tools.show_tool(tool['id'])
    print(tool_details.get('xml', 'No XML data available'))
```
This will provide partial XML descriptions of each tool, which can be useful for parsing and extracting key functionalities.

## Future Enhancements
- Improve XML parsing for tool descriptions.
- Optimize lookup functions for AI agent integration.
- Extend support for different Galaxy tool endpoints.
- Implement caching mechanisms for faster tool retrieval.

## License
This project is under the MIT License.

