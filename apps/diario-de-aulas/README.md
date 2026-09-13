# Diário de Aulas

App web de página única para acompanhar as aulas do semestre a partir dos planos de ensino
mantidos no vault do Obsidian.

## O que faz

- **Abas no topo** — `Painel` e uma aba por disciplina.
- **Painel** — a próxima aula em destaque, a agenda das aulas seguintes agrupada por dia e o
  andamento de cada disciplina (aulas dadas sobre o total e quantas já têm anotação).
- **Aba da disciplina** — as duas aulas anteriores e a próxima, uma abaixo da outra, cada uma
  com data, horário, sala, assunto e comentários. Abaixo, o cronograma completo recolhido.
- **Importar plano de ensino** — cole o markdown da nota e confirme a prévia do que foi lido.
  Reimportar a mesma disciplina atualiza o cronograma preservando os comentários já escritos.
- **Editar disciplina** — nome, curso, código ou turma, sala, horário padrão e cor. O horário pode
  ser aplicado de uma vez a todas as aulas do cronograma quando o horário da turma muda.
- **Exportar** — gera o diário em markdown (aula seguida das anotações) para salvar como `.md`
  ou copiar de volta para o vault.
- **Verificar duplicatas** — na aba da disciplina, funde aulas com a mesma data, horário e
  assunto (ignorando maiúsculas, acentos e espaçamento) em uma só, preservando as anotações de
  todas antes de apagar as repetidas. Roda também sozinho, uma vez, quando o app carrega — cobre
  o caso comum de importar o mesmo plano duas vezes.
- **Editar o cronograma completo** — ao expandir o cronograma, clique no horário, no assunto ou
  na unidade de qualquer aula para editar ali mesmo. Se outras aulas caírem no mesmo dia da
  semana e horário (as aulas semanais de uma turma, por exemplo), o app pergunta se a mudança
  deve valer para elas também.

## Formatos de plano de ensino reconhecidos

O leitor aceita tabelas e listas na mesma nota:

```markdown
---
disciplina: Cálculo Diferencial e Integral II
curso: Engenharia Civil
turma: MAT-1042 T2
sala: 305, Bloco B
horario: 19:00–20:40
---

# Cálculo Diferencial e Integral II

## Unidade 1

| Data       | Horário     | Assunto                          |
| ---------- | ----------- | -------------------------------- |
| 04/08/2026 | 19:00–20:40 | Integral indefinida e primitivas |

## Unidade 2

- 11/08/2026 — 19:00 — Integração por partes
- 18/08 — Teorema Fundamental do Cálculo
```

- **Datas**: `dd/mm`, `dd/mm/aaaa`, `dd/mm/aa`, `aaaa-mm-dd` e `12 de agosto`. Datas sem ano usam
  o ano informado no importador.
- **Horários**: `19:00`, `19h`, `19h00`, `19:00–20:40`, `19h às 20h40`. Aulas sem horário recebem
  o horário padrão da disciplina.
- **Unidades**: qualquer título de nível `##` ou mais profundo passa a valer para as aulas seguintes;
  uma coluna `Unidade`, `Módulo` ou `Semana` na tabela tem prioridade. A unidade aparece no
  cronograma completo e no markdown exportado — nos cards das aulas o espaço é da sala.
- **Frontmatter**: `disciplina`/`nome`, `curso`, `turma`/`codigo`, `sala`/`local` e `horario`
  preenchem os atributos da disciplina na importação, e podem ser ajustados depois no editor.
- **Colunas**: reconhecidas pelo nome (`Data`, `Horário`, `Assunto`/`Conteúdo`/`Tema`, `Unidade`).
  Sem cabeçalho reconhecível, a primeira coluna é a data e a segunda o assunto.
- Links internos do Obsidian (`[[nota|texto]]`) e marcações de negrito são limpos do assunto.

## Onde os dados ficam

Publicado como Artifact, o app guarda disciplinas, aulas e comentários no banco do próprio
artifact — os dados acompanham a conta em qualquer aparelho. Se esse armazenamento não estiver
disponível na sessão, o app avisa no topo e passa a guardar tudo no `localStorage` do navegador;
ao reconectar, o conteúdo local é enviado para a nuvem uma única vez.

## Como executar

`index.html` é a aplicação inteira — sem build e sem dependências, tirando as fontes do Google
Fonts. Abra o arquivo direto no navegador para desenvolver (nesse modo, os dados ficam apenas no
navegador) ou publique-o como Artifact declarando as capacidades `db` e `downloads`.
