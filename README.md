# Security Log Analyzer and Automated Alert System

A small, explainable Python tool that reads login logs (CSV), detects suspicious patterns using transparent rules, and generates alerts with supporting evidence for an analyst to review.

**Case study:** synthetic CSV login logs of a university web portal.

## Team

| Role | Name | ID |
|---|---|---|
| Student 1 | [Fatima rafiq] | [s2024105039] |
| Student 2 | [Amna jaffar] | [s2024105029] |

**Course:** [cyber security]
**Instructor:** [Zeeshan Akram]

## Aim

To design, implement and evaluate a Python-based security log analyzer that detects selected suspicious events in login logs and generates useful, traceable alerts.

## Features

- Parses and validates CSV logs; malformed rows are reported instead of crashing the tool
- Four detection rules with configurable thresholds
- Alerts include alert ID, timestamp, rule name, severity, affected entity and evidence
- Alerts saved to CSV, plus a command-line summary
- Evaluated with precision, recall, F1-score, false-positive rate and processing time

## Detection Rules

| Rule | Description | Severity |
|---|---|---|
| R1 | Repeated failed logins: 5 or more from one IP within 10 minutes | Medium / High |
| R2 | Success after failures: successful login after 3 or more failures for the same user and IP | High |
| R3 | Privileged role change: a role-change event granting administrator rights | High |
| R4 | Unusual event volume: 20 or more events from one IP within 1 minute | Medium |

## Input Format

CSV columns: `event_id, timestamp, username, source_ip, event_type, status`
(See `data/data_dictionary.md` for details.)

## Project Structure

```
data/    synthetic dataset and data dictionary
src/     parser, validator, rules, alerts, metrics, CLI
tests/   unit and integration tests
docs/    report and presentation
```

## How to Run

```bash
git clone https://github.com/Fatima755171n/security-log-analyzer.git
cd security-log-analyzer
python src/main.py --input data/synthetic_logs.csv --output alerts.csv
```

## Run Tests

```bash
python -m unittest discover tests
```

## Scope and Limitations

- Uses synthetic data only; no real or confidential logs
- Not a real-time or enterprise monitoring system
- No automated blocking or account disabling
- An alert is an indicator that needs investigation, not proof of an attack

## References

- Python 3 documentation: https://docs.python.org/3/
- NIST SP 800-61, Computer Security Incident Handling Guide
- MITRE ATT&CK: https://attack.mitre.org/
