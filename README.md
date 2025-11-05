# Aquário Entidades

Este repositório contém os dados das entidades (laboratórios, grupos estudantis, ligas, centros acadêmicos, empresas, etc.) exibidas na plataforma Aquário.

## Estrutura

O repositório está organizado por centro/unidade acadêmica. Atualmente, contém:

- `centro-de-informatica/` - Entidades do Centro de Informática da UFPB

Cada pasta de centro contém:
- Arquivos JSON individuais para cada entidade (um arquivo por entidade)
- Pasta `assets/` com as imagens/logos das entidades

## Como Adicionar uma Nova Entidade

### 1. Criar o arquivo JSON

Crie um novo arquivo JSON na pasta do centro correspondente (ex: `centro-de-informatica/`). O nome do arquivo deve ser um slug (letras minúsculas, hífens para espaços). Exemplos:
- `laboratorio-inteligencia-artificial.json`
- `grupo-pesquisa-redes.json`
- `liga-academica-software.json`

### 2. Estrutura do JSON

O arquivo JSON deve seguir esta estrutura:

```json
{
  "name": "Nome da Entidade",
  "subtitle": "Subtítulo opcional",
  "description": "Descrição detalhada da entidade. Pode usar quebras de linha com \\n.",
  "tipo": "LABORATORIO",
  "imagePath": "./assets/NomeArquivo.png",
  "contato_email": "email@exemplo.com",
  "instagram": "https://www.instagram.com/perfil/",
  "linkedin": "https://www.linkedin.com/company/empresa/",
  "website": "https://www.site.com",
  "location": "Localização física (opcional)",
  "founding_date": "2020-01-01",
  "order": 1,
  "people": [
    {
      "name": "Nome da Pessoa",
      "email": "email@exemplo.com",
      "role": "Cargo/Função",
      "profession": "Profissão"
    }
  ]
}
```

### 3. Propriedades Obrigatórias

- **`name`** (string): Nome da entidade
- **`tipo`** (string): Tipo da entidade (ver valores válidos abaixo)
- **`imagePath`** (string): Caminho para a imagem. Use `./assets/NomeArquivo.png` para imagens na pasta assets do mesmo centro
- **`contato_email`** (string): Email de contato da entidade
- **`people`** (array): Array de pessoas associadas à entidade (pode ser vazio `[]`)

### 4. Propriedades Opcionais

- **`subtitle`** (string): Subtítulo ou slogan da entidade
- **`description`** (string): Descrição detalhada
- **`instagram`** (string): URL completa do Instagram
- **`linkedin`** (string): URL completa do LinkedIn
- **`website`** (string): URL completa do website
- **`location`** (string): Localização física da entidade
- **`founding_date`** (string): Data de fundação no formato `YYYY-MM-DD`
- **`order`** (number): Ordem de exibição (quanto menor, mais acima aparece)

### 5. Valores Válidos para `tipo`

Os seguintes valores são aceitos para a propriedade `tipo`:

- `"LABORATORIO"` - Laboratórios de pesquisa
- `"CENTRO_ACADEMICO"` - Centros Acadêmicos
- `"ATLETICA"` - Atléticas
- `"LIGA_ESTUDANTIL"` - Ligas Estudantis
- `"GRUPO_ESTUDANTIL"` - Grupos Estudantis
- `"EMPRESA"` - Empresas
- `"OUTRO"` - Outros tipos

**Nota:** Valores legados são automaticamente convertidos (ex: `GRUPO_PESQUISA` → `GRUPO_ESTUDANTIL`).

### 6. Adicionar a Imagem

1. Adicione a imagem na pasta `assets/` do centro correspondente
2. Use um nome descritivo e consistente (ex: `TRIL.png`, `Aquario.png`)
3. No JSON, referencie com `./assets/NomeArquivo.png`

### 7. Formato do Array `people`

Cada pessoa no array deve ter:
- **`name`** (string): Nome completo
- **`email`** (string): Email (pode ser vazio `""`)
- **`role`** (string): Cargo ou função na entidade
- **`profession`** (string): Profissão ou título

### Exemplo Completo

```json
{
  "name": "TRIL",
  "subtitle": "Seize, Shape, Solve",
  "description": "Laboratório de pesquisa em inteligência artificial...",
  "tipo": "LABORATORIO",
  "imagePath": "./assets/TRIL.png",
  "contato_email": "tril@ci.ufpb.br",
  "instagram": "https://www.instagram.com/tril_lab/",
  "linkedin": "https://www.linkedin.com/company/trillab/",
  "website": "https://tril.ci.ufpb.br/",
  "location": "CI - 3o andar - CI-315",
  "order": 1,
  "people": [
    {
      "name": "Moises Dantas dos Santos",
      "email": "",
      "role": "Responsável",
      "profession": "Professor"
    }
  ]
}
```

## Adicionar um Novo Centro

Para adicionar entidades de um novo centro/unidade:

1. Crie uma nova pasta com o nome do centro (ex: `centro-de-ciencias-exatas/`)
2. Crie a estrutura de arquivos JSON e pasta `assets/` dentro dela
3. Os arquivos serão automaticamente detectados pelo sistema

## Validação

Após criar ou modificar um arquivo JSON, certifique-se de:
- O JSON está válido (sem erros de sintaxe)
- O arquivo de imagem existe na pasta `assets/`
- O `imagePath` aponta corretamente para a imagem
- O `tipo` usa um dos valores válidos
- As propriedades obrigatórias estão presentes

