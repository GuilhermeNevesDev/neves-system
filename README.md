# Neves System

Sistema web local criado para centralizar rotinas de apoio à operação de infraestrutura em uma única interface.

> **Edição de demonstração para GitHub.** Todos os registros, nomes de clientes, redes, técnicos, coordenadas, imagens e demais dados incluídos nesta versão são fictícios e existem somente para permitir a avaliação do projeto.

## O que é possível testar

- **Dashboard** com visão geral dos módulos.
- **Conversores**:
  - KMZ → Planilha;
  - Coordenadas → KMZ;
  - Localização → KMZ.
- **Atualizações DUDE** com cadastro, filtros, status, imagens e visualizador ampliado.
- **Viabilidade técnica** com cálculo de materiais, mão de obra, histórico e geração de PDF.
- **Mapeamento de Rede** com OLT, placa, PON, divisor, CTOs, ocupação, histórico e comparação de levantamentos.
- **Configurações** de cidades, OLTs, técnicos, preços e regras.
- Tema claro/escuro.

## Execução rápida no Windows

### Requisitos

- Windows 10 ou 11;
- **Python 3.11 ou superior**;
- conexão com a internet na primeira execução para instalar as dependências;
- Google Chrome somente para testar links encurtados do Google Maps no conversor de Localização.

### Primeira execução

1. Baixe o repositório em **Code → Download ZIP** e extraia a pasta.
2. Execute `Iniciar Neves System.bat`.
3. Na primeira vez, o sistema cria o ambiente virtual, instala as dependências e prepara automaticamente uma base fictícia.
4. O navegador abrirá em `http://127.0.0.1:5000`.

Login da demonstração:

```text
Usuário: admin
Senha: 1234
```

Se preferir separar a instalação da inicialização, execute primeiro `INSTALAR.bat` e depois `Iniciar Neves System.bat`.

## Arquivos prontos para testar os Conversores

A pasta `demo/arquivos_teste/` contém arquivos fictícios compatíveis com os três conversores:

```text
demo/arquivos_teste/
├── Rede_Exemplo.kmz
├── Coordenadas_Exemplo.xlsx
├── Localizacoes_Exemplo.xlsx
└── Relatorio_CTO_Exemplo.txt
```

O arquivo de Localizações usa URLs que já contêm latitude/longitude, então esse teste específico não depende de Chrome/Selenium.

## Restaurar a demonstração

Depois de editar/excluir registros durante os testes, execute:

```text
Resetar Dados da Demo.bat
```

O comando pede confirmação e recria o banco fictício inicial.

## Execução manual

### Windows

```bat
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
python demo\preparar_demo.py
python app.py
```

### Linux/macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python demo/preparar_demo.py
python app.py
```

Depois acesse `http://127.0.0.1:5000`.

## Tecnologias

- Python
- Flask
- SQLite
- HTML
- CSS
- JavaScript
- Pandas / OpenPyXL
- ReportLab
- Selenium (somente quando necessário para links encurtados)

## Estrutura resumida

```text
Neves-System/
├── app.py
├── routes/
├── services/
├── converters/
├── templates/
├── static/
├── demo/
│   ├── assets/
│   ├── arquivos_teste/
│   └── preparar_demo.py
├── database/
├── uploads/
├── requirements.txt
├── INSTALAR.bat
├── Iniciar Neves System.bat
└── .gitignore
```

## Privacidade dos dados

O repositório ignora automaticamente:

- `database/sistema.db`;
- chave local de sessão;
- uploads feitos no DUDE e Mapeamento;
- arquivos gerados;
- ambiente virtual `.venv`;
- variáveis `.env`.

A base exibida na primeira execução é criada pelo script `demo/preparar_demo.py` e contém somente dados fictícios.

## Observação

Esta versão foi preparada para **demonstração local e avaliação do projeto**. O servidor Flask abre apenas em `127.0.0.1`, portanto não publica o sistema na internet nem conecta a demonstração a outra instalação.

A identidade visual eventualmente presente no projeto é utilizada apenas no contexto demonstrativo da ferramenta; marcas pertencem aos seus respectivos titulares.
