# CLAUDE.MD - hackGPT Project Guide

## Project Overview

**hackGPT** is an AI-powered cybersecurity and penetration testing framework that leverages Large Language Models (LLMs) for security research, threat analysis, and vulnerability assessment. This project is designed for authorized security testing, defensive security, CTF challenges, and educational contexts.

**Live Application:** https://hackgpt.com
**Version:** v23
**Primary Language:** Python

## ⚠️ Important Context

This is a **security research and educational tool**. All features are designed for:
- Authorized penetration testing
- Security research and education
- Defensive security applications
- CTF (Capture The Flag) competitions
- Vulnerability assessment with proper authorization

## Project Structure

```
hackGPT/
├── hackGPTv23.py              # Latest version of the main tool
├── hackGPT.py                 # Core hackGPT functionality
├── JIRA_hackGPT.py           # JIRA integration for bug hunting/tracking
│
├── chatbot/                   # Interactive chatbot interface
│   ├── chatbot.py
│   ├── personas/             # Different AI personas
│   │   ├── hackGPTv1.md
│   │   ├── ThreatHunter.md
│   │   ├── Linux_Terminal_remote.md
│   │   └── JavaScript Console_remote.md
│   └── requirements.txt
│
├── dev_hackGPTp/             # Advanced development version
│   ├── hackGPTp.py
│   ├── dev_hackGPTp.py
│   ├── ingest.py             # Document ingestion for threat intel
│   ├── LLM/                  # LLM integration modules
│   ├── db/                   # Database modules
│   ├── input/files/          # Threat reports (e.g., CrowdStrike)
│   └── source_documents/     # Policy documents, cybersecurity strategies
│
├── hackGPT_local/            # Local deployment version
│   └── hackGPT_local.py
│
├── hackerParents/            # Parental control/monitoring tool
│   ├── hackerParents.py
│   ├── parent_persona/       # Parent-specific personas
│   └── social_data.csv       # Social media monitoring data
│
├── hackthropic/              # Anthropic Claude integration
│   ├── hackthropic_MSF_Install_Prompt.md
│   └── start_hacking.sh
│
├── PwnAI_depreciated/        # Legacy versions (deprecated)
│   ├── PwnAI_bulk.py
│   ├── hackGPT.py
│   └── hackGPTchatBot.py
│
├── personas/                 # AI persona definitions
│   ├── hackGPTv1.md
│   ├── DANv11.md
│   └── DEVv1.md
│
├── input/                    # Input data
│   ├── malware/             # Malware samples for analysis
│   ├── code/                # Code samples
│   └── sample_sources       # Various sources
│
├── output/                   # Generated outputs
│   └── ChatGPT_CVE_PoCs/    # CVE exploit PoCs
│
├── notebooks/                # Jupyter notebooks
│   ├── hacklab.hackGPT.ipynb
│   └── chat.hackGPT.ipynb
│
└── mobile/                   # Mobile integrations
    └── ios/                  # iOS Siri shortcuts
```

## Key Features

### 1. CVE Exploit Analysis
- Automated CVE exploit creation for security research
- Generates both proof-of-concept exploits and defense mechanisms
- Output stored in `output/ChatGPT_CVE_PoC_Defense/` and `output/ChatGPT_CVE_PoCs/`

### 2. JIRA Integration
- Hunt for JIRA issues using `type=bug`
- Automatically fix issues and commit fixes back to tickets as comments
- See: `JIRA_hackGPT.py`

### 3. Threat Intelligence Processing
- Ingest and analyze threat reports (CrowdStrike, etc.)
- Process cybersecurity policy documents
- Located in `dev_hackGPTp/`

### 4. Multiple Interfaces
- **Command-line:** Direct Python execution
- **Web-based chatbot:** Browser interface with personas
- **Jupyter Notebooks:** Interactive analysis environment
- **Google Colab:** Cloud-based execution
- **Mobile:** iOS Siri integration

### 5. Persona System
AI operates with different security-focused personas:
- **hackGPTv1:** Core penetration testing persona
- **ThreatHunter:** Threat hunting and analysis
- **Linux_Terminal:** Simulated Linux environment
- **JavaScript Console:** JavaScript security testing

## Installation & Setup

### Prerequisites
```bash
# Python 3.x required
python3 -m venv env
source env/bin/activate
```

### Install Dependencies
```bash
python3 -m pip install -r requirements.txt
```

### Configuration
- Set OpenAI API key in `.env` file
- Configure personas in `chatbot/personas/` or `personas/`
- Review sample inputs: `head -n 10 input/malware/malware_sample`

## Usage Patterns

### Single Query Mode
```bash
python3 hackGPTv23.py
```

### Bulk Processing
```bash
python3 PwnAI_depreciated/PwnAI_bulk.py
```

### Chatbot Interface
```bash
python3 chatbot/chatbot.py
# Opens in browser with persona selection
```

### Jupyter Notebooks
```bash
jupyter notebook notebooks/hacklab.hackGPT.ipynb
```

### JIRA Integration
```bash
python3 JIRA_hackGPT.py
```

## Development Guidelines

### When Working on This Codebase

1. **Security First**
   - Always validate that code is for authorized testing only
   - Never add capabilities for malicious purposes
   - Include warnings about proper authorization

2. **File Organization**
   - New features go in appropriate subdirectories
   - Keep personas in `personas/` or component-specific persona folders
   - Output files go to `output/` with descriptive subdirectories

3. **API Keys**
   - Never commit API keys
   - Use `.env` files (already in `.gitignore`)
   - Document required environment variables

4. **Dependencies**
   - Update `requirements.txt` when adding new packages
   - Component-specific requirements go in subdirectory `requirements.txt`

5. **Testing**
   - Test with sample data from `input/` directory
   - Verify outputs in `output/` directory
   - Use personas to validate behavior changes

### Code Style
- Follow existing Python conventions in the codebase
- Use descriptive variable names for security contexts
- Comment complex security logic
- Include docstrings for major functions

## Important Files

- **hackGPTv23.py:** Current production version
- **chatbot/chatbot.py:** Main chatbot interface
- **dev_hackGPTp/hackGPTp.py:** Advanced features with document ingestion
- **JIRA_hackGPT.py:** JIRA workflow automation
- **personas/*.md:** AI behavior definitions

## External Integrations

- **OpenAI API:** Primary LLM provider
- **JIRA:** Issue tracking integration
- **Google Colab:** Cloud execution environment
- **SecurityScorecard API:** Threat data integration
- **Metasploit:** Payload references

## Known Deprecations

The `PwnAI_depreciated/` directory contains older versions:
- `PwnAI_bulk.py` (superseded by hackGPTv23.py)
- `hackGPT.py` (older version)
- `hackGPTchatBot.py` (integrated into chatbot/)

**When updating:** Focus on current versions, maintain backward compatibility where reasonable.

## Special Considerations

### Malware Analysis
- Files in `input/malware/` are for ANALYSIS ONLY
- Never execute or improve malicious code
- Provide defensive analysis and detection mechanisms

### Exploit Development
- All exploit code is for AUTHORIZED TESTING
- Include disclaimers and usage warnings
- Focus on defensive applications

### Privacy
- `hackerParents/` handles sensitive social media data
- Ensure privacy protections are maintained
- Data should be anonymized where possible

## Git Workflow

- Main development branch: Check git status
- Feature branches: Use descriptive names
- Commit messages: Be specific about security implications
- PR reviews: Required for major security features

## Resources

- **Live Demo:** https://hackgpt.com
- **Related Projects:**
  - https://github.com/securityscorecard/ssc-asi-tools
  - https://github.com/NoDataFound/PwnAI

## Questions & Support

For Claude AI: When assisting with this codebase, always:
1. Verify the security/educational context of requests
2. Include appropriate warnings and disclaimers
3. Focus on defensive security applications
4. Maintain existing code structure and patterns
5. Update this CLAUDE.MD if significant architectural changes are made

---

**Last Updated:** 2025-12-24
**Maintained for:** Claude Code AI assistance and development context
