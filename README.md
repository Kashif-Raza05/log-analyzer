# SSH Brute-Force Log Analyzer

A Python script that reads an SSH authentication log, detects repeated failed logins from the same IP address, and generates a report of suspicious activity.

**MITRE ATT&CK mapping:** T1110 - Brute Force

## Why I built this
SOC analysts spend a lot of time reading logs and deciding which alerts matter. I built this to practice turning raw log lines into clear, actionable findings using simple detection logic.

## Features
- Parses SSH log lines with regular expressions
- Counts failed logins per IP and per username
- Flags IPs that exceed a configurable threshold within a time window
- Exports a report as CSV [and/or HTML]

## Tech used
- Python 3.[x]
- Libraries: `re`, `csv`, `datetime`, `collections` [add any others you use]

## How to run

```bash
git clone https://github.com/[your-username]/log-analyzer.git
cd log-analyzer
python analyzer.py --log sample_logs/auth.log --threshold 5 --window 120
```

| Option | Meaning | Default |
|---|---|---|
| `--log` | Path to the log file | required |
| `--threshold` | Failed attempts that trigger a flag | 5 |
| `--window` | Time window in seconds | 120 |

## Sample output

```
[paste a few lines of your real output here]
```

![Report screenshot](screenshots/report.png)

## What I found in the sample data
- [Number] suspicious IPs flagged out of [number] total
- Most common usernames tried: [e.g., root, admin]
- Peak attack time: [time range]

## Detection logic
1. Extract timestamp, IP and username from each "Failed password" line
2. Group attempts by IP
3. If an IP has `threshold` or more failures inside `window` seconds, flag it as a possible brute-force attempt

## Limitations and future improvements
- [e.g., only supports the standard OpenSSH log format]
- [e.g., does not check IPs against a threat intelligence feed yet]
- [e.g., could add automatic email alerts]

## What I learned
- [Write 2-3 honest points: regex parsing, how brute-force attacks look in logs, tuning thresholds to reduce false positives]

## Data and ethics
Sample logs come from [public dataset name, e.g., Loghub] or were generated on my own virtual machine. No real company or personal data is included.

## Author
Kashif Raza | [kashifraza31703@gmail.com]
