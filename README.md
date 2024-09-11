# git-ignore-automation-task
script escrito em powershell para automatizar a adição de um arquivo .gitignore sempre que inicializar um novo repositório Git
isso parte do preceito que eu acredito, devemos facilitar o processo de inicialização de projetos tanto quanto possível, pra isso eu acho uma boa ideia criar tarefas e rotinas na sua máquina, pisso inclui coisass como agendar commits e pushs, que injclusive pode encontrar em outrro repositório meu

## recomendações e como usar
eu sugiro que você adicione uma automação no seu perfil do Powershell, para adicionar o `gitignore` assim que usar `git init`
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
dica:
 personalizE o ambiente do PowerShell, como definir funções, aliases e variáveis de ambiente.
aprenda PowerShell e Bash, automatize rotinas, e dedique-se ao que importa, viver a vida, fazer coisas utéis, do it less boring, make more smarter
o conteúdo do git ignore já está embutido no script shell, mas para facilitar o uso geral e customizado, disponibilizei o arquivo, porém apenas para python, modifique conrfome necessitar, abraço!
