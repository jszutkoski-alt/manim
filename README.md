# Animações educacionais com Manim

Repositório de animações desenvolvidas em um Projeto de Iniciação à Docência (PID), com o objetivo de apoiar o ensino e a aprendizagem por meio de visualizações matemáticas e científicas produzidas com [Manim Community](https://www.manim.community/).

## Sobre o projeto

Este projeto reúne o código-fonte de animações criadas como recursos didáticos. As cenas buscam representar conceitos, relações e processos de maneira visual e dinâmica, contribuindo para a explicação de conteúdos em sala de aula e para a produção de materiais educacionais reutilizáveis.

Além de disponibilizar as animações, o repositório pretende documentar o processo de criação e facilitar a adaptação dos materiais por estudantes, professores e demais pessoas interessadas em programação aplicada à educação.

## Objetivos

- Produzir animações que auxiliem na apresentação de conceitos matemáticos e científicos.
- Explorar o Manim como ferramenta para criação de recursos didáticos.
- Organizar e documentar o código das cenas desenvolvidas no PID.
- Incentivar a integração entre programação, visualização e ensino.
- Permitir que os materiais sejam estudados, executados e adaptados para outros contextos educacionais.

## Tecnologias

- [Python](https://www.python.org/)
- [Manim Community](https://www.manim.community/)
- LaTeX, utilizado pelo Manim na renderização de expressões matemáticas

## Organização do repositório

Uma estrutura possível para o projeto é:

```text
.
├── scenes/          # Código-fonte das animações
│   ├── tema_01/
│   └── tema_02/
├── assets/          # Imagens, dados e outros recursos utilizados
├── examples/        # Exemplos simples ou cenas de demonstração
├── requirements.txt
└── README.md
```

As pastas podem ser reorganizadas conforme novos conteúdos forem adicionados.

## Como executar

### 1. Pré-requisitos

Instale o Python e as dependências de sistema indicadas na [documentação de instalação do Manim](https://docs.manim.community/en/stable/installation.html).

### 2. Prepare o ambiente

Clone o repositório e entre na pasta do projeto:

```bash
git clone URL_DO_REPOSITORIO
cd NOME_DO_REPOSITORIO
```

Crie e ative um ambiente virtual:

```bash
python -m venv .venv
source .venv/bin/activate
```

No Windows, use:

```powershell
.venv\Scripts\activate
```

Instale as dependências:

```bash
pip install -r requirements.txt
```

Caso o arquivo `requirements.txt` ainda não tenha sido criado, instale o Manim diretamente:

```bash
pip install manim
```

### 3. Renderize uma animação

Para executar uma cena, informe o arquivo e o nome da classe correspondente:

```bash
manim -pql scenes/exemplo.py NomeDaCena
```

Nesse comando:

- `-p` abre o vídeo após a renderização;
- `-ql` utiliza qualidade baixa e é útil durante o desenvolvimento.

Para gerar o vídeo final em alta qualidade, use:

```bash
manim -pqh scenes/exemplo.py NomeDaCena
```

Consulte o arquivo de cada tema para identificar as cenas disponíveis e eventuais instruções específicas.

## Exemplo mínimo

```python
from manim import *


class OlaManim(Scene):
    def construct(self):
        titulo = Text("Olá, Manim!")
        self.play(Write(titulo))
        self.wait()
```

Para renderizar:

```bash
manim -pql exemplo.py OlaManim
```

## Uso educacional

As animações podem ser utilizadas como apoio em aulas, apresentações, estudos dirigidos e materiais digitais. Ao adaptar uma cena, recomenda-se considerar os objetivos de aprendizagem, o público e o contexto em que a visualização será apresentada.

## Como contribuir

Contribuições são bem-vindas. Você pode colaborar corrigindo problemas, aprimorando a documentação, refatorando cenas ou propondo novas animações.

Antes de enviar uma contribuição:

1. Crie uma branch para a alteração.
2. Mantenha o código legível e identifique claramente as cenas.
3. Teste a renderização dos arquivos modificados.
4. Descreva a finalidade pedagógica e as principais mudanças no pull request.

## Autoria e créditos

Projeto desenvolvido no contexto de uma iniciativa de iniciação à docência. Informações sobre instituição, curso, coordenação, participantes e período de execução poderão ser acrescentadas nesta seção.

## Licença

A licença do projeto ainda deve ser definida. Antes de reutilizar ou redistribuir o código e os materiais, consulte os responsáveis pelo repositório.

