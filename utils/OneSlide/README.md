# One-Slide — Acompanhamento

Acompanhamento do projeto Hp-DAC. Um slide por desenvolvedor por objetivo por semana.

| Arquivo | Uso |
|---|---|
| `One-Slide_PT.pptx`, slide 1 | Modelo com orientações e exemplos — ler uma vez |
| `One-Slide_PT.pptx`, slide 2 | Slide em branco — duplicar este a cada semana |

---

## O ciclo

O trabalho corre em **macrociclos de seis semanas**.

| Fase | O que acontece |
|---|---|
| **Abertura** (dia 1) | Sessão em grupo para mapear as dependências cruzadas, depois 1:1 com cada desenvolvedor para definir o objetivo e a lista de atividades do ciclo |
| **Semanas 1–6** | Reunião semanal, um slide por desenvolvedor |
| **Fechamento** (semana 6) | Revisão contra o objetivo: o que foi entregue, o que não foi, por quê |

**Reunião semanal.** Os slides circulam antes, para que ninguém leia
status em voz alta. 
---

## Preenchendo o slide

### Cabeçalho — `X.X. ACOMPANHAMENTO - RESPONSÁVEL`, `DD/MM/AAAA - DD/MM/AAAA`

Número sequencial, nome do responsável e o intervalo de datas da semana. O
número corre ao longo de todo o projeto, de modo que o arquivo se acumula
como registro histórico: `2.4` é ciclo 2, semana 4.

> `2.4 ACOMPANHAMENTO - A. Lorenzoni` · `25/08/2026 - 31/08/2026`

### OBJETIVO — *para que serve este ciclo*

**Definido na abertura e inalterado nos seis slides semanais.**

Uma frase, declarando um resultado com uma condição verificável.

> Entregar um modelo em regime permanente da bomba de calor comercial que
> reproduza o COP medido com desvio de ±10% na faixa de temperatura de fonte
> quente de 60 a 95 °C.

Não *"trabalhar no modelo da bomba de calor"* — sem condição de conclusão,
nenhuma semana pode falhar contra ele.

### ATIVIDADES — *o que foi acordado fazer e em que estágio está cada item*

Itens **fixados na abertura do ciclo**. A lista é idêntica
toda semana; só a formatação muda conforme os itens migram entre estados.

| Estado | Formatação |
|---|---|
| Concluída | Cinza-claro, ~~tachado~~ |
| Em andamento | Preto |
| Planejada | Cinza-claro |

Ordene concluída → em andamento → planejada. Os itens sobem ao longo do ciclo
e o bloco esvazia de baixo para cima, de modo que o slide se lê como um
*burn-down* sem que ninguém precise desenhar um.

**Cada item começa com verbo no infinitivo**, na mesma forma nos três estados
— *Comissionar, Validar, Quantificar, Ajustar, Medir, Selecionar, Decidir,
Documentar*.

O verbo força uma condição de conclusão. Evite *Estudar, Analisar,
Investigar, Trabalhar em, Melhorar, Explorar* — não têm estado final e
ocuparão o ciclo inteiro. Se o trabalho for mesmo aberto, escreva-o como uma
decisão: *"Decidir até S3 se continuamos com R1336mzz(Z) ou recuamos para uma
cascata."*

**Cada item leva uma data-alvo de conclusão**, ao final da linha.

> ~~Ajustar o mapa de desempenho do compressor aos dados do fabricante — 05/09~~
> **Comissionar a bomba de calor no reator DAC 15TA — 19/09**
> Validar o modelo em regime permanente com os ensaios de 60–80 °C — 03/10

**Se a data escorregar, mantenha a original entre parênteses:**
`— 03/10 (alvo 19/09)`. Sem isso a data é apenas reescrita a cada semana, e o
slide deixa de registrar que houve atraso — que é justamente a informação
útil.

O teste na abertura: *o que eu vou olhar para concordar que isto está
concluído?* Se não há resposta, o verbo está errado.

### PRÓXIMOS PASSOS — *o que será verdade na próxima reunião*

Apenas a semana seguinte, o restante do ciclo já está em ATIVIDADES. Toda
linha rastreável a uma atividade, começando por verbo.

Preenchido em **duas etapas**. Antes da reunião, o responsável redige os
passos propostos; é essa versão que circula. Durante a reunião, as
contribuições da equipe são acrescentadas ao mesmo bloco, e a versão
pós-reunião é o registro, salve por cima da que circulou, para haver um só
arquivo por semana.

> **Redigido antes**
> Repetir o ensaio de 90 °C com o medidor Coriolis recalibrado — 03/09.
>
> **Acrescentado na reunião**
> Verificar o isolamento da linha de sucção antes de repetir; pode explicar a
> superestimativa de 8% — 03/09.

Quem digita durante a reunião não é quem apresenta. As pessoas formulam
sugestões com muito mais precisão quando as veem sendo escritas.

### RESULTADOS — *o que sabemos agora que não sabíamos na semana passada*

O maior bloco do slide: **uma figura ou tabela, mais uma frase dizendo o que
ela mostra.** Evidência, não atividade. Dados, não narrativa.

---

## O que muda quando

| Bloco | Definido em | Muda |
|---|---|---|
| Cabeçalho | semanalmente | número, datas |
| OBJETIVO | abertura | nunca, dentro de um ciclo |
| ATIVIDADES | abertura | apenas formatação e datas |
| PRÓXIMOS PASSOS | semanalmente | redigido, depois ampliado na reunião |
| RESULTADOS | semanalmente | toda semana |

---

## Convenções

**Figuras.** Use o
[padrão de gráficos do projeto](../src/hpdac/utils/README.md), no tamanho
140 × 85 mm. O mesmo estilo que produz as figuras do relatório produz estas,
então nada é redesenhado depois.

**Nomes** 

Usar o seguinte padrão para nomear os arquivos: "One-Slide_Grupo_Data" e colocar em sua respectiva pasta no drive. 



