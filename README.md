# SPIRED-Fitness MCP

SPIRED-Fitness MCP server for protein modeling, extracted from the [official SPIRED-Fitness tutorials](https://github.com/Gonglab-THU/SPIRED-Fitness).

## Overview
This SPIRED-Fitness MCP server provides three protein analysis tools using ProtTrans models. Here we have 3 main scripts for protein analysis:

## Installation

```bash
# Create and activate virtual environment
mamba env create -p ./env python=3.11 pip -y
mamba activate ./env

pip install click einops pandas biopython tqdm loguru sniffio
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install --ignore-installed fastmcp
```
Download the [model parameters](https://zenodo.org/records/10675405) and move it into the `data/model` folder.

## Local usage
### 1. Structure prediction
```shell
python scripts/run_spired.py --fasta examples/test.fasta --output examples/spired --repo repo/SPIRED-Fitness
```

### 2. Fitness prediction
```shell
python scripts/run_spired_fitness.py --fasta examples/test.fasta --output examples/spired --repo repo/SPIRED-Fitness
```

### 3. Stability prediction
```shell
python scripts/run_spired_stab.py --fasta examples/test.fasta --output examples/spired --repo repo/SPIRED-Fitness
```


### Install MCP Server
```shell
fastmcp install claude-code mcp-servers/prottrans_mcp/src/prottrans_mcp.py --python mcp-servers/prottrans_mcp/env/bin/python
fastmcp install gemini-cli mcp-servers/prottrans_mcp/src/prottrans_mcp.py --python mcp-servers/prottrans_mcp/env/bin/python
```

### Call MCP service
1. Structure prediction
```markdown
Can you help train a ProtTrans model for data @examples/case2.1_subtilisin/ and save it to 
@examples/case2.1_subtilisin/prot-t5_fitness using the ProtTrans mcp server with ProtT5-XL model.

Please convert the relative path to absolution path before calling the MCP servers. 
```

2. Fitness prediction
```markdown
```

3. Stability prediction