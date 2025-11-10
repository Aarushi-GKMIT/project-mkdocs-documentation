This repository contains mkdocs documentation for the project "Deployment Pipeline" 
It contains functional and usecase documentation of the project.
It defines project's functional and business use cases.


Commands to run Mkdocs


1. Create and Activate Virtual Environment

```bash
# Create a virtual environment
python -m venv .venv

# Activate it
# On macOS/Linux:
source .venv/bin/activate

# On Windows:
.venv\Scripts\activate

# Install MkDocs and dependencies
pip install mkdocs
pip install mkdocs-material


pip install -r requirements.txt

# Run the Documentation Server
mkdocs serve

Build Static Documentation
mkdocs build

# Theme 
pip install mkdocs-material

Added data modelling to the doucmentation. In this three tables User, Project and Deployment are there along with the ER Diagram and Indexing.

# For mermaid
pip install mkdocs-mermaid2-plugin



