# Diagnósticos 

## Demostração com falhas Provacadas 

### 1 - Verificar Diretorio 
```bash
# comando: 
pwd 

# saida: 
/c/dpw-execicios 

# Diagnostico:
Diretorio correto 

```
### 2 - Verificar package.json  
```bash
# comando: 
cat package.json 

# saida: 
{
  "name": "dpw-exercicios",
  "version": "1.0.0",
  "private": "true",
  "description": "",
  "main": "index.js",
  "scripts": {
    "verificar": "node --version && pnpm --version"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devEngines": {
    "packageManager": {
      "name": "pnpm",
      "version": "^11.22.0",
      "onFail": "download"
    }
  },
  "type": "module",
  "devDependencies": {
    "prettier": "^3.9.6"
  }
}

# Diagnostico 
esta tudo ok com o package.json 
```

### 3 - Verificar pasta node_modules 
```bash

# comando:
ls node_modules 

# saida:
ls : Não é possível localizar o caminho 'C:\dpw-exercicios\node_modules' porque ele não existe.

# diagnostico:
A pasta node_modules nao existe no ambiente 
``` 

```bash
# comando para restaurar o ambiente:
npm install 

# saida: 
added 1 packege, and audited 2 packages in 1s 
```
