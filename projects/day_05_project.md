# Day 5 Project — AI Configuration and File Management Utility

## Objective
Build a command-line utility that reads a JSON configuration, validates required fields, writes a report and records safe events in a log. No API credentials are needed.

## Folder structure
~~~text
day_05_project/
    app.py
    config.json
    output/
    logs/
~~~

## config.json
~~~json
{
  "application_name": "TechPhile Learning Utility",
  "provider": "demo",
  "model_name": "sample-model",
  "temperature": 0.2
}
~~~

## app.py
~~~python
import json
import logging
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent
CONFIG_PATH = BASE_DIR / "config.json"
OUTPUT_DIR = BASE_DIR / "output"
LOG_DIR = BASE_DIR / "logs"

OUTPUT_DIR.mkdir(exist_ok=True)
LOG_DIR.mkdir(exist_ok=True)

logging.basicConfig(
    filename=LOG_DIR / "application.log",
    level=logging.INFO,
    format="%(asctime)s %(levelname)s %(message)s"
)


def load_config(path):
    with open(path, "r", encoding="utf-8") as file:
        config = json.load(file)

    required = ["application_name", "provider", "model_name"]
    for field in required:
        if field not in config:
            raise ValueError(f"Missing required setting: {field}")
    return config


def write_report(config, path):
    with open(path, "w", encoding="utf-8") as file:
        file.write(f"Application: {config['application_name']}\\n")
        file.write(f"Provider: {config['provider']}\\n")
        file.write(f"Model: {config['model_name']}\\n")


def main():
    logging.info("Utility started")
    try:
        config = load_config(CONFIG_PATH)
        report = OUTPUT_DIR / "configuration_report.txt"
        write_report(config, report)
        logging.info("Configuration report created")
        print(f"Report created: {report}")
    except FileNotFoundError:
        logging.error("Configuration file missing")
        print("Configuration file is missing.")
    except json.JSONDecodeError:
        logging.error("Configuration contains invalid JSON")
        print("Configuration file is not valid JSON.")
    except ValueError as error:
        logging.error("Configuration validation failed: %s", error)
        print("Configuration problem:", error)


if __name__ == "__main__":
    main()
~~~

## Walkthrough
- Path(__file__).resolve().parent finds the script's folder, not the terminal's current folder.
- mkdir(exist_ok=True) creates output folders if absent.
- basicConfig writes safe log messages to a file.
- json.load parses configuration into a dictionary.
- The required-field loop validates before using values.
- with open closes the report file.
- Specific except branches handle expected failures separately.
- The main guard starts the utility only when run directly.

## Run
Windows: py app.py  
macOS/Linux: python3 app.py

Expected: a report-created message. Open output/configuration_report.txt and confirm the three fields. Inspect logs/application.log.

## Test cases
| Test | Change | Expected |
|---|---|---|
| TC01 | Valid JSON | Report created |
| TC02 | Rename config.json | Friendly missing-file message |
| TC03 | Break JSON syntax | Invalid JSON message |
| TC04 | Remove model_name | Validation message |
| TC05 | Run twice | Report safely regenerated |
| TC06 | Inspect log | Events present, no credentials |

Restore the valid JSON after negative tests.

## Extensions
1. Validate temperature is numeric and between 0 and 1.
2. Move configuration validation to config_utils.py.
3. Add a safe DEBUG event.
4. Add an append-only audit file for report creation.
5. Explain why secrets must not be committed.

## Submission
Submit app.py, non-secret config.json, generated report, test table and a short explanation of exception handling and logging.
