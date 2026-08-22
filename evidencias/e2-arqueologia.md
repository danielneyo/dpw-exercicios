# Perguntas

```powershell 
| 1 | quantos commits o repositorios tem? |
| 2 | Qual foi o primeiro commmit, e em que data?|
| 3 | Quem mais modificou packages/core/injector/injector.ts? |
| 4 | O que mudou no último commit que troucou esse arquivo? | 
| 5 | Quantos commmits foram feitos nos últimos 90 dias | 
```
# Respostas 
```powershell 
| 1 | Foram feitos: 21648 commits / comando usado : git rev-list --count HEAD |  
| 2 | O primeiro commit foi: f7c8d10fb Initial commit / comando usado: git log --reverse --online --date=short | 
| 3 | Mais modificou foi: 6586c0d98 Kamil Myśliwiec 2026-02-13 , seu nome aparece 11 vezes de 2014 a 2026 / comando usado: git log --pretty=format:"%h %an %ad" --date=short -- packages/core/injector/injector.ts | 
| 4 | O que mudou no ultimo commit foi: 
commit 5d1b19bca65c7b25dd5dc27c0a6384b8015ee43d
Merge: b6bdd79c4 a112f3fbd
Author: Kamil Myśliwiec <mail@kamilmysliwiec.com>
Date:   Fri Aug 14 16:05:35 2026 +0200

    Merge branch 'master' into v12.0.0
    
    Resolves conflicts between the v12 ESM/vitest migration and master:
    - Ported the SseSignal/AbortController SSE feature into the ESM codebase
      (sse-signal.decorator, router-response-controller, router-execution-context,
      interceptors-consumer transformDeferred rewrite)
    - Converted master's chai/sinon/mocha test additions to vitest style
    - Kept v12 sample structure (oxlint/vitest) while adopting master's
      renovate dependency bumps
    - Regenerated package-lock.json / comando usado: git log -p -1 -- packages/core/injector/injector.ts |
| 5 | Nos últimos 90 dias foram feitos: 718 commits / comando usado: git log --since="90 days ago" --oneline | MeasureObject -Line |