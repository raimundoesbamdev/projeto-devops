from pathlib import Path

content = """# Projeto DevOps

## Descrição

Aplicação web simples desenvolvida com HTML e CSS, servida pelo Nginx em um contêiner Docker. O projeto utiliza Git e GitHub para versionamento do código e Jenkins para automatizar as etapas de construção, implantação e teste da aplicação.

## Tecnologias utilizadas

- HTML e CSS
- Nginx
- Docker
- Git e GitHub
- Jenkins

## Pré-requisitos

Para executar o projeto, é necessário ter instalado:

- Git
- Docker
- Um navegador web

Para executar o pipeline de automação, também é necessário ter o Jenkins configurado com acesso ao repositório e ao Docker.

## Como usar

### 1. Clonar o repositório

```bash
git clone <URL_DO_REPOSITORIO>
cd <PASTA_DO_PROJETO>
```

Substitua `<URL_DO_REPOSITORIO>` pela URL do repositório Git e `<PASTA_DO_PROJETO>` pelo nome da pasta criada.

### 2. Construir a imagem Docker

Na pasta do projeto, execute:

```bash
docker build -t minha-app .
```

### 3. Executar a aplicação

```bash
docker run -d --name minha-app -p 8080:80 minha-app
```

Abra no navegador:

http://localhost:8080

### 4. Atualizar a aplicação

Depois de modificar os arquivos HTML ou CSS, envie as alterações para o repositório:

```bash
git add .
git commit -m "Descreve a alteração"
git push
```

Para aplicar as mudanças na versão em execução, reconstrua a imagem e recrie o contêiner:

```bash
docker build -t minha-app .
docker rm -f minha-app
docker run -d --name minha-app -p 8080:80 minha-app
```

**Atenção:** esses comandos removem o contêiner chamado `minha-app` e o criam novamente. Eles não removem a imagem nem os arquivos do projeto.

### 5. Executar pelo Jenkins

Se o Jenkins estiver configurado para usar o repositório Git e o arquivo `Jenkinsfile`:

1. Abra a interface do Jenkins.
2. Entre no job configurado para o projeto.
3. Clique em **Build Now**.
4. Abra a execução e confira o resultado do pipeline.

O endereço da interface do Jenkins depende da configuração do ambiente. Em uma configuração local que use a porta `8081`, acesse:

http://localhost:8081

## Estrutura esperada dos arquivos

```text
projeto-devops/
├── Dockerfile
├── Jenkinsfile
├── index.html
└── style.css
```

## Observações

- A porta `8080` precisa estar livre para executar a aplicação conforme os comandos acima.
- O nome `minha-app` precisa estar disponível como nome de contêiner.
- O pipeline do Jenkins depende das configurações do job e das permissões de acesso ao Docker.
"""
path = Path("/mnt/data/README.md")
path.write_text(content, encoding="utf-8")
print(f"Arquivo criado: {path} ({path.stat().st_size} bytes)")
