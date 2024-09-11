# git-ignore-automation-task
script escrito em powershell para automatizar a adição de um arquivo .gitignore sempre que inicializar um novo repositório Git
isso parte do preceito que eu acredito, devemos facilitar o processo de inicialização de projetos tanto quanto possível, pra isso eu acho uma boa ideia criar tarefas e rotinas na sua máquina, pisso inclui coisass como agendar commits e pushs, que injclusive pode encontrar em outrro repositório meu

## recomendações e como usar
eu sugiro que você adicione uma automação no seu perfil do Powershell, para adicionar o `gitignore` assim que usar `git init`

Para PowerShell (usando init-git)
criea pasta de scritps no diretório do usuário:
`echo $HOME\scripts\init-git.ps1`

Adicione a seguinte linha ao seu arquivo de perfil do PowerShell ($PROFILE):
```Powershell
function init-git {
    param (
        [string]$dir = (Get-Location)
    )
    . "$HOME\scripts\init-git.ps1" -dir $dir
}
```
depois reinicie o perfil: `. $PROFILE`


Para git bash:
crie um Diretório para Armazenar o Script:
`mkdir -p $HOME/scripts
`
Crie o Script git-init.sh:

Crie o arquivo git-init.sh no diretório scripts:
`nano $HOME/scripts/git-init.sh
`
Cole o seguinte conteúdo no arquivo git-init.sh:
```
#!/bin/bash

# Inicializa o repositório Git
git init

# Adiciona um arquivo .gitignore pré-pronto para Python
cat <<EOL > .gitignore
# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# C extensions
*.so

# Distribution / packaging
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
share/python-wheels/
*.egg-info/
.installed.cfg
*.egg
MANIFEST

# PyInstaller
#  Usually these files are written by a python script from a template
#  before PyInstaller builds the exe, so as to inject date/other infos into it.
*.manifest
*.spec

# Installer logs
pip-log.txt
pip-delete-this-directory.txt

# Unit test / coverage reports
htmlcov/
.tox/
.nox/
.coverage
.coverage.*
.cache
nosetests.xml
coverage.xml
*.cover
*.py,cover
.hypothesis/
.pytest_cache/
cover/

# Translations
*.mo
*.pot

# Django stuff:
*.log
local_settings.py
db.sqlite3
db.sqlite3-journal

# Flask stuff:
instance/
.webassets-cache

# Scrapy stuff:
.scrapy

# Sphinx documentation
docs/_build/
docsrc/_build/

# PyBuilder
target/

# Jupyter Notebook
.ipynb_checkpoints

# IPython
profile_default/
ipython_config.py

# pyenv
.python-version

# pipenv
# According to pypa/pipenv#598, it is recommended to include Pipfile.lock in version control.
# However, in case of collaboration, if having platform-specific dependencies or dependencies
# having no cross-platform support, pipenv may install dependencies that don't work, or not
# install all needed dependencies.
#Pipfile.lock

# PEP 582; used by e.g. github.com/David-OConnor/pyflow
__pypackages__/

# Celery stuff
celerybeat-schedule
celerybeat.pid

# SageMath parsed files
*.sage.py

# Environments
.env
.venv
env/
venv/
ENV/
env.bak/
venv.bak/

# Spyder project settings
.spyderproject
.spyproject

# Rope project settings
.ropeproject

# mkdocs documentation
/site

# mypy
.mypy_cache/
.dmypy.json
dmypy.json

# Pyre type checker
.pyre/

# pytype static type analyzer
.pytype/

# Cython debug symbols
cython_debug/

# PyCharm
.idea/

# VS Code
.vscode/
EOL

# Adiciona e faz commit do .gitignore
git add .gitignore
git commit -m "Adiciona arquivo .gitignore para Python"
```
Torne o Script Executável:

No terminal, torne o script `git-init.sh` executável:
`chmod +x $HOME/scripts/git-init.sh`
Crie um Alias no Git:

Adicione um alias ao Git para usar o script git-init.sh sempre que você usar gi init

dica:
 personalizE o ambiente do PowerShell, como definir funções, aliases e variáveis de ambiente.
aprenda PowerShell e Bash, automatize rotinas, e dedique-se ao que importa, viver a vida, fazer coisas utéis, do it less boring, make more smarter
o conteúdo do git ignore já está embutido no script shell, mas para facilitar o uso geral e customizado, disponibilizei o arquivo, porém apenas para python, modifique conrfome necessitar, abraço!
