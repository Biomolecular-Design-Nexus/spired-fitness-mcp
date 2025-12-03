# SPIRED-Fitness MCP

SPIRED-Fitness MCP server for protein modeling, extracted from the [official SPIRED-Fitness tutorials](https://github.com/Gonglab-THU/SPIRED-Fitness).

## Overview
This SPIRED-Fitness MCP server provides three protein analysis tools. Here we only use Spired-Stab in the mcp service for stability prediction.

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
fastmcp install claude-code mcp-servers/spired_fitness_mcp/src/spired_fitness_mcp.py --python mcp-servers/spired_fitness_mcp/env/bin/python
fastmcp install gemini-cli mcp-servers/spired_fitness_mcp/src/spired_fitness_mcp.py --python mcp-servers/spired_fitness_mcp/env/bin/python
```

### Call MCP service
Test data paths
- /home/xux/Desktop/ProteinMCP/ProteinMCP/mcp-servers/spired-fitness_mcp/examples/sequences.fasta
- /home/xux/Desktop/ProteinMCP/ProteinMCP/mcp-servers/spired-fitness_mcp/examples/data.csv
- /home/xux/Desktop/ProteinMCP/ProteinMCP/examples/case2.1_subtilisin/data.csv

#### Stability prediction
```markdown
Can you predict the stabilities for variants in @examples/case2.1_subtilisin/data.csv and save it as @examples/case2.1_subtilisin/data.csv_spired_stab.csv using the spired_fitness_mcp.

Please convert the relative path to absolution path before calling the MCP servers. 
```