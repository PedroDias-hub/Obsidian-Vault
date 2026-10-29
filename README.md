# 📚 Obsidian Vault — Estudos de Ciência da Computação

Repositório pessoal de estudos organizado no **Obsidian**, reunindo conteúdos de **Matemática**, **Ciência da Computação**, **Programação** e disciplinas da **UNIP**.

O objetivo deste vault é centralizar anotações, resumos, fórmulas, exercícios e roadmaps de estudo em arquivos Markdown (`.md`), utilizando links internos do Obsidian para conectar os conteúdos.

## 📌 Conteúdos

Atualmente, o vault possui materiais sobre:

- **Matemática**
  - Álgebra
  - Álgebra Linear
  - Cálculo 0
  - Cálculo I
  - Cálculo II
  - Cálculo III
  - Fórmulas e tabelas de consulta
  - Exercícios

- **Programação**
  - C++
  - Assembly x86-64
  - Estruturas de dados
  - Algoritmos
  - Memória e ponteiros
  - Programação orientada a objetos
  - Ferramentas de desenvolvimento

- **Faculdade — UNIP**
  - Cálculo
  - Spring Boot
  - JDBC
  - Padrão DAO
  - Banco de dados H2
  - Spring MVC
  - Conteúdos do curso de Ciência da Computação

## 📂 Estrutura do repositório

```text
Obsidian Vault/
├── .obsidian/              # Configurações do Obsidian
├── Faculdade/
│   └── UNIP/
│       ├── Cálculo/
│       ├── Spring Boot/
│       └── UNIP_CienciaDaComputacao_1Sem/
├── Matemática/
│   ├── 00 - Índice/
│   ├── Álgebra/
│   ├── Álgebra Linear/
│   ├── Cálculo 0/
│   ├── Cálculo I/
│   ├── Cálculo II/
│   ├── Cálculo III/
│   ├── Exercícios/
│   ├── Fórmulas/
│   └── Livros e Referências/
├── Programação/
│   ├── Assembly/
│   └── C++/
└── Início.md               # Página inicial do vault
```

## 🚀 Instalação

### Pré-requisitos

Para utilizar o vault da forma recomendada, instale:

- [Obsidian](https://obsidian.md/)
- [Git](https://git-scm.com/) — opcional, caso queira clonar e atualizar o repositório pelo terminal

> Os arquivos são Markdown e podem ser abertos em qualquer editor de texto, mas o Obsidian é recomendado para utilizar corretamente os links internos e a navegação entre as notas.

### Opção 1 — Clonar com Git

Abra o terminal na pasta em que deseja armazenar o vault e execute:

```bash
git clone URL_DO_REPOSITORIO.git
```

Depois, entre na pasta clonada:

```bash
cd NOME_DO_REPOSITORIO
```

Substitua `URL_DO_REPOSITORIO.git` pela URL HTTPS do repositório no GitHub.

### Opção 2 — Baixar pelo GitHub

1. Clique em **Code**.
2. Selecione **Download ZIP**.
3. Extraia o arquivo `.zip` em uma pasta de sua preferência.

## 🧠 Abrindo no Obsidian

1. Abra o **Obsidian**.
2. Clique em **Open folder as vault** / **Abrir pasta como cofre**.
3. Selecione a pasta raiz do repositório que contém:

```text
.obsidian/
Faculdade/
Matemática/
Programação/
Início.md
```

4. Confirme a abertura do vault.
5. Abra o arquivo `Início.md` para acessar o mapa geral dos conteúdos.

As configurações principais do Obsidian já estão presentes na pasta `.obsidian` do repositório.

## 🔄 Atualizando o vault com Git

Caso o repositório tenha sido clonado com Git, para baixar novas alterações execute:

```bash
git pull
```

Para enviar alterações próprias ao GitHub:

```bash
git add .
git commit -m "Atualiza anotações"
git push
```

## 📝 Como navegar

O ponto inicial recomendado é:

```text
Início.md
```

A partir dele, é possível acessar os principais mapas do vault.

Alguns conteúdos também possuem seus próprios arquivos `README.md` e índices internos, como:

```text
Matemática/README.md
Matemática/Cálculo 0/README.md
Matemática/Cálculo II/README.md
Matemática/Cálculo III/README.md
Programação/Assembly/README.md
Faculdade/UNIP/Spring Boot/README.md
```

Os links no formato:

```text
[[Nome da Nota]]
```

são **WikiLinks do Obsidian** e permitem navegar diretamente entre notas relacionadas.

## 🛠️ Tecnologias e formatos

- Obsidian
- Markdown
- Git
- GitHub
- WikiLinks do Obsidian

Os conteúdos de estudo abordam tecnologias e linguagens como:

- C++
- Assembly x86-64
- Java
- Spring Boot
- JDBC
- SQL

## 🎯 Objetivo do projeto

Este repositório funciona como uma base de conhecimento pessoal para organizar a evolução dos estudos em Ciência da Computação, permitindo:

- concentrar anotações em um único lugar;
- criar conexões entre assuntos relacionados;
- acompanhar roadmaps de estudo;
- consultar fórmulas e resumos rapidamente;
- registrar conteúdos da faculdade;
- manter o material versionado com Git e GitHub.

## ⚠️ Observações

Este é um vault de estudos em constante atualização. Algumas notas podem estar incompletas, sendo revisadas ou expandidas conforme o avanço dos estudos.

As configurações incluídas em `.obsidian` podem alterar aparência, plugins nativos e organização da interface ao abrir o vault.

## 📄 Licença

O conteúdo deste repositório foi criado para fins de estudo e organização pessoal.

Caso o projeto seja disponibilizado publicamente e você queira permitir reutilização formal do conteúdo, recomenda-se adicionar uma licença ao repositório, como **MIT** ou **Creative Commons**, de acordo com o tipo de material publicado.
