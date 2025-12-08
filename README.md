# SPIRED-Stab MCP

SPIRED-Stab MCP server for protein stability prediction, extracted from the [official SPIRED-Fitness tutorials](https://github.com/Gonglab-THU/SPIRED-Fitness).

## Overview
This SPIRED-Fitnesss provides three protein analysis tools. Here we only use Spired-Stab in the mcp service for stability prediction.

## Installation

```bash
# Create and activate virtual environment
mamba env create -p ./env python=3.11 pip -y
mamba activate ./env

pip install click einops pandas biopython tqdm loguru sniffio
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install --ignore-installed fastmcp
```
Download the [model parameters](https://zenodo.org/records/10675405) and move it into the `scripts/data/model` folder.

## Local usage
### 1. Stability prediction
```shell
python scripts/run_SPIRED-Stab.py --fasta_file examples/sequences.fasta --wt_fasta_file examples/wt.fasta --device cuda:1
```

## MCP usage
### Install MCP Server
```shell
fastmcp install claude-code tool-mcps/spired_stab_mcp/src/spired_stab_mcp.py --python tool-mcps/spired_stab_mcp/env/bin/python
fastmcp install gemini-cli tool-mcps/spired_stab_mcp/src/spired_stab_mcp.py --python tool-mcps/spired_stab_mcp/env/bin/python
```

### Call MCP service
Test data paths
- /home/xux/Desktop/ProteinMCP/ProteinMCP/tool-mcps/spired_stab_mcp/examples/sequences.fasta
- /home/xux/Desktop/ProteinMCP/ProteinMCP/tool-mcps/spired_stab_mcp/examples/data.csv
- /home/xux/Desktop/ProteinMCP/ProteinMCP/examples/case2.1_subtilisin/data.csv

#### Stability prediction
```markdown
Can you predict the stabilities for variants in @examples/case2.1_subtilisin/data.csv using the spired_stab_mcp.

Please convert the relative path to absolution path before calling the MCP servers. 
```