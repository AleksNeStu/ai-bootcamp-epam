# ai-bootcamp-epam
GenAI Solutions Development Bootcamp [EPAM] 2024

# How to setup
```sh
curl -sSL https://install.python-poetry.org | python3 - --version 1.7.0
poetry py3.11 ai-poc
poetry config virtualenvs.in-project true
poetry env use 3.11
source .venv/bin/activate
poetry config virtualenvs.prompt 'ai-poc-py3.11'
poetry config --list
```

# How to run
```sh
git https://github.com/AleksNeStu/ai-bootcamp-epam.git
poetry install --no-root
source .venv/bin/activate
```