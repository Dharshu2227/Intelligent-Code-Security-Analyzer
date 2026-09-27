# Intelligent-Code-Security-Analyzer

An AI-assisted code security analysis system that detects common security issues, analyzes code complexity, retrieves relevant secure-coding knowledge, calculates a risk score, and generates a final security report.

## Project Overview

The **AI Code Security Analyzer** is designed to help developers identify potential security vulnerabilities and code-quality problems in Python source code.

The system combines:

* **Bandit** for Python security analysis
* **Radon** for code complexity analysis
* **TF-IDF** for security knowledge retrieval
* **Risk scoring** for overall security assessment
* **CSV report generation** for analysis results

## Features

### 1. Security Vulnerability Detection

The project uses Bandit to detect potential security problems in Python code.

Examples include:

* Hardcoded passwords
* Unsafe subprocess usage
* `shell=True`
* Possible command injection
* Other common Python security issues

### 2. Code Complexity Analysis

Radon is used to analyze the complexity of Python functions.

The analyzer provides:

* Cyclomatic complexity
* Complexity rank
* Function-level complexity information

### 3. Security Knowledge Base

The system contains knowledge about:

* Coding standards
* Common programming bugs
* Secure coding practices
* Input validation
* SQL injection prevention
* Command injection prevention
* Password security
* Hardcoded credentials
* Sensitive information handling
* Least privilege

### 4. Knowledge Retrieval

TF-IDF and cosine similarity are used to retrieve security guidance relevant to detected issues.

For example:

```text
Detected Issue:
Hardcoded password found in source code

Retrieved Knowledge:
Password Storage

Recommendation:
Passwords should never be stored as plain text.
Use a strong password hashing algorithm with appropriate salt.
```

### 5. Risk Score

The system combines security findings and code complexity to calculate an overall risk score.

Severity points are assigned according to the detected security issue severity.

The resulting report contains:

* Risk score
* Risk level
* Security findings
* Code complexity
* Security recommendations

### 6. Final CSV Report

The analyzer generates:

```text
final_risk_report.csv
```

The report contains information such as:

| Field              | Description                      |
| ------------------ | -------------------------------- |
| File               | Source file containing the issue |
| Line               | Line number of the issue         |
| Issue              | Security issue detected          |
| Severity           | Bandit severity                  |
| Confidence         | Bandit confidence                |
| Test_ID            | Bandit test identifier           |
| Security_Rule      | Retrieved security rule          |
| Recommendation     | Secure-coding recommendation     |
| Similarity         | Retrieval similarity score       |
| Average_Complexity | Average Radon complexity         |
| Risk_Score         | Calculated risk score            |
| Risk_Level         | Overall risk level               |

## Technologies Used

* Python
* Google Colab
* Bandit
* Radon
* Pandas
* Scikit-learn
* TF-IDF
* Cosine Similarity

## Project Structure

```text
AI-Code-Security-Analyzer/
│
├── README.md
│
├── AI_Code_Security_Analyzer.ipynb
│
├── final_risk_report.csv
│
└── sample.py
```

> The exact files may vary depending on the final Colab notebook version.

## How to Run

### Step 1: Open Google Colab

Open the project notebook in Google Colab.

### Step 2: Install Dependencies

Run:

```python
!pip install -q bandit radon
```

The notebook also uses:

```text
pandas
scikit-learn
```

which are commonly available in Google Colab.

### Step 3: Provide Python Source Code

The analyzer can work with a Python source file such as:

```text
sample.py
```

### Step 4: Run Security Analysis

Bandit analyzes the source code for potential security issues.

Example:

```python
!bandit -r sample.py -f json -o bandit_report.json
```

### Step 5: Run Complexity Analysis

Radon analyzes the complexity of functions:

```python
!radon cc sample.py -j
```

### Step 6: Retrieve Security Knowledge

The detected security issues are matched against the security knowledge base using TF-IDF and cosine similarity.

### Step 7: Generate Risk Report

The system combines the analysis results and creates:

```text
final_risk_report.csv
```

## Example Analysis

For example, if the source code contains:

```python
password = "admin123"
```

Bandit can identify a potential hardcoded password issue.

The knowledge retrieval system can then retrieve information about password storage and provide a secure-coding recommendation.

Another example:

```python
subprocess.call(user_input, shell=True)
```

The analyzer can identify a potential command-injection-related security issue and retrieve relevant secure-coding guidance.

## Output

The final output is:

```text
final_risk_report.csv
```

Example workflow:

```text
Python Source Code
        |
        v
     Bandit
        |
        v
Security Findings
        |
        +----------------+
        |                |
        v                v
   Knowledge Base      Radon
        |                |
        v                v
Security Guidance   Complexity
        |                |
        +-------+--------+
                |
                v
           Risk Scoring
                |
                v
     final_risk_report.csv
```

## Advantages

* Automated Python security analysis
* Detects common security issues
* Provides secure-coding recommendations
* Includes code complexity analysis
* Uses retrieval-based security knowledge
* Generates a structured CSV report
* Can be executed in Google Colab
* Useful for educational and development purposes

## Limitations

* The current implementation focuses on Python source code.
* Bandit detection is limited to the vulnerabilities supported by Bandit.
* TF-IDF retrieval depends on the quality and coverage of the knowledge base.
* The risk score is a project-defined heuristic and should not be treated as a definitive security rating.
* The analyzer does not replace a professional security audit or penetration test.

## Future Enhancements

Possible future improvements include:

* Support for additional programming languages
* Larger secure-coding knowledge base
* Semantic/vector-based retrieval
* Integration with an LLM for automated explanations
* Web-based dashboard
* Real-time code analysis
* PDF/HTML security reports
* GitHub repository scanning
* Improved risk scoring
* Historical comparison of security reports

## Conclusion

The **AI Code Security Analyzer** combines static security analysis, code complexity measurement, knowledge retrieval, and risk scoring into a single workflow.

It helps developers identify potential security problems and understand recommended secure-coding practices while producing a structured security report for further review.

## Disclaimer

This project is intended for educational, research, and development purposes. Security findings should be manually reviewed before making production decisions.
