# OpenVPN-Fingerprinting

Three methods to detect and fingerprint OpenVPN traffic, developed as a research project.

## Methods

| Method | File | Approach |
|--------|------|----------|
| **Active Server Probing** | `active server probing.ipynb` | Sends crafted packets to a target server and analyzes responses to identify OpenVPN vs other services |
| **Entropy-Based Detection** | `entropy based detection.ipynb` | Calculates Shannon entropy of UDP payloads on port 1194 — encrypted VPN traffic has high entropy |
| **Opcode-Based Detection** | `opcode based detection.ipynb` | Parses OpenVPN control channel opcodes to identify the handshake pattern: HARD_RESET -> CONTROL -> ACK -> DATA |

## Project Structure

```
OpenVPN-Fingerprinting/
├── README.md
├── requirements.txt
├── LICENSE
├── active server probing.ipynb
├── entropy based detection.ipynb
├── opcode based detection.ipynb
├── result.xlsx
├── Re-search paper.pdf
├── VPN data sets.zip
└── data/                          # Extracted dataset
    └── VPN data sets/
        ├── 13.201.81.174/
        │   ├── call traffic.pcap
        │   ├── game traffic.pcap
        │   ├── https-traffic.pcap
        │   └── vpn traffic.pcap
        └── 43.204.236.255/
            ├── call traffic.pcap
            ├── game traffic.pcap
            ├── https-traffic.pcap
            └── vpn traffic.pcap
```

## Setup

```bash
pip install -r requirements.txt
```

Extract the dataset:
```bash
# Already extracted to data/ folder, or:
unzip "VPN data sets.zip" -d data/
```

## Usage

Run each notebook with Jupyter:
```bash
jupyter notebook "active server probing.ipynb"
jupyter notebook "entropy based detection.ipynb"
jupyter notebook "opcode based detection.ipynb"
```

## Results

See `result.xlsx` for detection results across both methods. The dataset includes:
- **VPN traffic** (positive class) — should be detected
- **Call, Game, HTTPS traffic** (negative class) — should NOT be flagged as VPN

## Requirements

- Python 3.10+
- Python 3.10 or compatible
- scapy, numpy, pandas, openpyxl

## Authors

- Yalamarthi Kuladeep
- [Co-author name]
