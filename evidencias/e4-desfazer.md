## Tabela de Cenário 
```powershell
| # | Cenário   |
| 1 | Edite um arquivo e quero descartar a alteração (ainda não fiz add) |
|____comando: git status
|
|____ saida:
PS C:\dpw-exercicios> git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   rascunho.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        evidencias/e4-desfazer.md
    no changes added to commit (use "git add" and/or "git commit -a")
```
```powershell
| 2 | Fiz git add do arquivo errado e quero tirá-lo do stage 
|____comando: git restore rascunho.txt
|____comando: git status 
|
|____saida: 
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        evidencias/e4-desfazer.md

nothing added to commit but untracked files present (use "git add" to track)

| 2 | Tira do stage
|___comando: git add rascunho.txt 
|___comando: git status
|
|___saida:
PS C:\dpw-exercicios> git add rascunho.txt
PS C:\dpw-exercicios> git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   rascunho.txt

| 2 | Remover do stage:
|___comando: git restore --staged rascunho.txt 
|___comando: git status 
|
|___saida: 
S C:\dpw-exercicios> git restore --staged rascunho.txt
PS C:\dpw-exercicios> git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   rascunho.txt

```
```bash
| 3 | A mensagem do último commit está errada (inda não fiz push)
|___comando: git restore rascunho.txt  # --> descarta qualquer alteração pendente 
|___comando: git commit -m "mensagem" --allow-empty # --> fazendo um commit com mensagem errada 
|___comando: git log --oneline -3 # --> para ver o historico
|
|___saida: 
2ba8336 (HEAD -> main) mensagem errada
59eb921 test: criando o arquivo rascunho.txt para testes do e4
1044c77 (origin/main) docs: adicionando imagem e atualizando evidencia de conflito 

# corrijindo o erro 
|___comando: git commit --amend -m "mensagem ->  mensagem certa"
|___comando: git log --oneline -3
|___saida: 
2ba8336 (HEAD -> main) mensagem errada
59eb921 test: criando o arquivo rascunho.txt para testes do e4
1044c77 (origin/main) docs: adicionando imagem e atualizando evidencia de conflito 

```bash
| 4 | Quero desfazer o último commit, mas manter as alterações no working directory 
|___comando: git log --oneline -3 # --> para verificar o historico 
|___comando: git reset --soft HEAD~1 # --> para desfazer o ultímo commit 
|__saida git log --oneline -3:
1044c77 (origin/main) docs: adicionando imagem e atualizando evidencia de conflito
641c837 docs: adicionando evidencias do e3-conflito  # podemos vê que a linha que referenciava o commit foi apagada 
|___saida git status:
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)On branch main 

```

```bash
| 5 | Quero reverter um commit já enviado para o remoto 
|___commit ja enviado para o github
|___comandos: git add rascunho.txt 
              git commit -m "feat: commit para testar reverter"
              git push origin main 
|___comando: git log oneline -3 
|___saida: 
6a1916d (HEAD -> main, origin/main) test: criando o arquivo rascunho.txt para testes do e4
3700cda atualização e3-conflito "docs: adicionando quebra de linha"
282e678 atualização "docs: adicionando os links que estavem faltando"

| 5 | executar a reversao e envia para p github 
|__comandos: git revert HEAD --no-edit 
|__saida:
[main 653501c] Revert "test: criando o arquivo rascunho.txt para testes do e4"
 1 file changed, 2 deletions(-)
 delete mode 100644 rascunho.txt

|__comando:git push origin main
|__saida:
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (2/2), 271 bytes | 38.00 KiB/s, done.
Total 2 (delta 1), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/danielneyo/dpw-exercicios.git
   6a1916d..653501c  main -> main

|___comando: git log oneline -3 # mais uma vez para ver o historico kkkk que pancada prof.helio 
|___saida:
653501c (HEAD -> main, origin/main) Revert "test: criando o arquivo rascunho.txt para testes do e4"
6a1916d test: criando o arquivo rascunho.txt para testes do e4
3700cda atualização e3-conflito "docs: adicionando quebra de linha" 

|__comando: git reflog -10 
|__saida:
653501c (HEAD -> main, origin/main) HEAD@{0}: revert: Revert "test: criando o arquivo rascunho.txt para testes do e4"
6a1916d HEAD@{1}: pull origin main --rebase (finish): returning to refs/heads/main
6a1916d HEAD@{2}: pull origin main --rebase (pick): test: criando o arquivo rascunho.txt para testes do e4
3700cda HEAD@{3}: pull origin main --rebase (start): checkout 3700cda00f272b6ff01ce848931627a4f5ca66db
59eb921 HEAD@{4}: reset: moving to HEAD~1
2ba8336 HEAD@{5}: commit: mensagem errada
59eb921 HEAD@{6}: commit: test: criando o arquivo rascunho.txt para testes do e4
1044c77 HEAD@{7}: commit: docs: adicionando imagem e atualizando evidencia de conflito
641c837 HEAD@{8}: commit: docs: adicionando evidencias do e3-conflito
813b804 HEAD@{9}: commit (merge): fix: Resolvendo o conflito de merge entre titulo-a e titulo-b
```