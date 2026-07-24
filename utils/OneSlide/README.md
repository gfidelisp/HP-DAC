# One-Slide — Acompanhamento

Acompanhamento do projeto Hp-DAC. Um slide por desenvolvedor por semana —
objetivo, atividades, próximos passos, resultados, obstáculos.

O formato é deliberadamente pequeno. Um slide que não comporta tudo obriga a
escolher o que importa, e essa escolha é a maior parte do valor.

| Arquivo | Uso |
|---|---|
| `One-Slide_PT.pptx`, slide 1 | Modelo com orientações e exemplos — ler uma vez |
| `One-Slide_PT.pptx`, slide 2 | Slide em branco — duplicar este a cada semana |

---

## Layout

O slide tem duas colunas de larguras diferentes, e a diferença é intencional.

| Coluna | Blocos | Largura |
|---|---|---|
| Esquerda | OBJETIVO, ATIVIDADES, PRÓXIMOS PASSOS | 40 % |
| Direita | RESULTADOS, OBSTÁCULOS | 59 % |

**RESULTADOS ocupa sozinho 44 % do slide.** Isso força a reunião a começar
pela evidência, e não pela narração do que foi feito. Se o bloco maior está
vazio na terceira semana seguida, isso é a informação mais importante do
slide.

---

## O ciclo

O trabalho corre em **macrociclos de seis semanas** com **duas semanas de
intervalo** (*cooldown*).

| Fase | O que acontece |
|---|---|
| **Abertura** (dia 1) | Sessão em grupo para mapear as dependências cruzadas, depois 1:1 com cada desenvolvedor para definir o objetivo e a lista de atividades do ciclo |
| **Semanas 1–6** | Reunião semanal, um slide por desenvolvedor |
| **Fechamento** (semana 6) | Revisão contra o objetivo: o que foi entregue, o que não foi, por quê |
| **Intervalo** (2 semanas) | Artigos, relatórios, congressos, pendências. Sem compromissos de ciclo |

O intervalo não é folga a ser reaproveitada. Sem ele, prazos de congresso e
revisões de artigo vazam para dentro do ciclo, todo objetivo escorrega por
motivos que ninguém planejou, e a fronteira das seis semanas deixa de
significar alguma coisa.

**Reunião semanal.** Os slides circulam 24 horas antes, para que ninguém leia
status em voz alta. A reunião abre pela leitura dos **PRÓXIMOS PASSOS da
semana anterior** — três ou quatro linhas, trinta segundos, cada uma recebe
um sim ou um não — e depois gasta o tempo em obstáculos e decisões. Dez
minutos por pessoa.

---

## Preenchendo o slide

### Cabeçalho — `1. ACOMPANHAMENTO - RESPONSÁVEL`, `DD/MM/AAAA - DD/MM/AAAA`

Número sequencial, nome do responsável e o intervalo de datas da semana. O
número corre ao longo de todo o projeto, de modo que o arquivo se acumula
como registro histórico: `2.4` é ciclo 2, semana 4.

> `2.4 ACOMPANHAMENTO - A. Lorenzoni` · `25/08/2026 - 31/08/2026`

### OBJETIVO — *para que serve este ciclo*

**Definido na abertura e inalterado nos seis slides semanais.** Essa
constância é o ponto: é a referência fixa contra a qual cada semana é
julgada. Reescrevê-lo é como um ciclo se torna, silenciosamente, aquilo que
por acaso foi feito.

Uma frase, declarando um resultado com uma condição verificável.

> Entregar um modelo em regime permanente da bomba de calor comercial que
> reproduza o COP medido com desvio de ±10% na faixa de temperatura de fonte
> quente de 60 a 95 °C.

Não *"trabalhar no modelo da bomba de calor"* — sem condição de conclusão,
nenhuma semana pode falhar contra ele.

### ATIVIDADES — *o que foi acordado fazer e em que estágio está cada item*

De três a seis itens, **fixados na abertura do ciclo**. A lista é idêntica
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
Documentar*. Nunca conjugar conforme o estado: um item precisa ser a mesma
string na semana 2 e na semana 5, ou o olho não consegue segui-lo entre
slides.

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

Apenas a semana seguinte — o restante do ciclo já está em ATIVIDADES. Toda
linha rastreável a uma atividade, começando por verbo, com **responsável e
data**.

Preenchido em **duas etapas**. Antes da reunião, o responsável redige os
passos propostos; é essa versão que circula. Durante a reunião, as
contribuições da equipe são acrescentadas ao mesmo bloco, e a versão
pós-reunião é o registro — salve por cima da que circulou, para haver um só
arquivo por semana.

> **Redigido antes**
> Repetir o ensaio de 90 °C com o medidor Coriolis recalibrado — A. Lorenzoni, 03/09.
>
> **Acrescentado na reunião**
> Verificar o isolamento da linha de sucção antes de repetir; pode explicar a
> superestimativa de 8% (P. Faria) — A. Lorenzoni, 03/09.

Marque a origem entre parênteses. Não por crédito — quando uma hipótese se
mostrar errada na semana 5, as iniciais apontam de volta para a conversa que
a produziu.

**Uma sugestão só vira compromisso quando tem responsável e data.** O que for
levantado ou é assumido aqui, ou é estacionado em ATIVIDADES como item
planejado, ou vai para o backlog do próximo ciclo. Recusar o compromisso é o
desfecho normal: um ciclo tem apetite fixo, e aceitar toda sugestão é como
seis semanas de trabalho viram nove.

De duas a quatro linhas redigidas antes, até seis depois das contribuições.
Acima disso a semana está sobrecarregada.

Quem digita durante a reunião não é quem apresenta. As pessoas formulam
sugestões com muito mais precisão quando as veem sendo escritas.

### RESULTADOS — *o que sabemos agora que não sabíamos na semana passada*

O maior bloco do slide: **uma figura ou tabela, mais uma frase dizendo o que
ela mostra.** Evidência, não atividade. Dados, não narrativa.

A frase diz o que a evidência *significa*, com um número — a mesma disciplina
de uma legenda de figura.

> O COP cai de 3,4 para 2,1 quando a temperatura da fonte quente sobe de 60
> para 95 °C; o modelo superestima em 8% acima de 85 °C.

Não *"gráfico de COP versus temperatura"*. Se nenhum número couber, pergunte
se já existe um resultado.

**Mantenha a mesma figura ao longo do ciclo e deixe-a preencher.** Um gráfico
de validação que ganha pontos semana a semana conta a história melhor do que
seis figuras sem relação, e a versão da semana 6 é a que vai para o relatório
ANP.

Gere a figura no tamanho do bloco — **140 × 85 mm** — e não na versão de
190 mm do relatório. Reduzida para caber, uma legenda de 13 pt chega a cerca
de 9 pt e fica ilegível no projetor:

```python
fig, ax = plt.subplots(figsize=(140 * MM, 85 * MM))
```

Um resultado negativo é um resultado. Uma semana sem evidência nova diz isso
em uma linha e mantém a figura anterior no lugar.

### OBSTÁCULOS — *o que impede o cumprimento do objetivo*

Somente obstáculos. Não progresso, não um resumo das atividades. Duas ou três
linhas — um slide com seis deixou de priorizar.

**O teste:** se o desenvolvedor consegue resolver sozinho dentro da semana,
não é obstáculo, é uma atividade que ainda não foi feita.

Cada linha carrega o obstáculo, seu efeito sobre o objetivo, quem o remove e
até quando. O responsável é quem *pode* removê-lo, que normalmente não é o
desenvolvedor.

> Dados do fabricante cobrem apenas condensação de 35–75 °C, deixando a faixa
> de 85–120 °C exigida pelo DAC sem sustentação — G. Peixer, até 05/09

> Entrega da bomba de calor na PUCRS postergada para 15/09, atrasando o
> comissionamento em ~2 semanas — G. Peixer, até 05/09 — *aberto desde S2*

Mantenha a marca *aberto desde* em tudo que for carregado de uma semana para
outra. Um obstáculo na terceira semana é uma falha de gestão, não um fato do
projeto, e o slide deve dizê-lo sem que ninguém precise falar.

Quando não houver nada, escreva **Nenhum**. Uma caixa em branco se lê como
campo não preenchido, não como semana limpa.

---

## O que muda quando

| Bloco | Definido em | Muda |
|---|---|---|
| Cabeçalho | semanalmente | número, datas |
| OBJETIVO | abertura | nunca, dentro de um ciclo |
| ATIVIDADES | abertura | apenas formatação e datas |
| PRÓXIMOS PASSOS | semanalmente | redigido, depois ampliado na reunião |
| RESULTADOS | semanalmente | toda semana |
| OBSTÁCULOS | semanalmente | toda semana |

Dois blocos estáticos, três vivos. Se o OBJETIVO ou a lista de ATIVIDADES
mudar no meio do ciclo, isso é mudança de escopo e merece uma conversa
explícita — não uma edição silenciosa. É esse sinal que o formato existe para
dar.

---

## Convenções

**Etapas ANP.** Prefixe cada atividade com sua etapa — `[E1]`–`[E4]`. Seis
semanas de slides podem então ser filtradas por etapa quando um relatório
vencer, em vez de reconstruir o mapeamento de memória.

**Figuras.** Use o
[padrão de gráficos do projeto](../src/hpdac/utils/README.md), no tamanho
140 × 85 mm. O mesmo estilo que produz as figuras do relatório produz estas,
então nada é redesenhado depois.

**Arquivos.** Um arquivo por pessoa, um slide por semana, acrescentado ao
final. O arquivo é o registro — nunca sobrescreva o slide da semana anterior.

```
tracking/
├── One-Slide_PT.pptx           # modelo, não editar
├── ciclo-02/
│   ├── lorenzoni.pptx
│   ├── faria.pptx
│   └── nakashima.pptx
```

---

## Trabalho de descoberta

Ciclos de seis semanas vêm do desenvolvimento de produto, onde o mecanismo é
tempo fixo e escopo variável. Pesquisa nem sempre reduz escopo: uma bancada
comissiona ou não comissiona, um modelo converge ou não converge.

Separe então dois tipos de atividade.

**Trabalho de construção** — instalar, instrumentar, implementar, integrar —
aceita entregável e data. É a maior parte das etapas E1 e E4.

**Trabalho de descoberta** — *este conceito chega a 120 °C com COP aceitável?*
— aceita um **ponto de decisão**, não um entregável: *"Decidir até S3 se
continuamos com a abordagem A ou recuamos para B."* Isso converte um risco
aberto em uma escolha agendada, que é algo que um líder técnico consegue
administrar. Uma atividade de descoberta com resultado prometido é uma
promessa que ninguém pode cumprir.

---

## Modos de falha

**Tudo permanece verde.** Relatar um obstáculo parece admitir fracasso, então
as pessoas esperam até que seja inegável — momento em que o ciclo já acabou.
Diga uma vez na abertura, e com convicção: levantar um obstáculo é um pedido,
não uma confissão, e um ciclo em que nenhum apareceu provavelmente tinha
objetivos fáceis demais.

**PRÓXIMOS PASSOS vira lista de desejos.** Só se evita lendo em voz alta as
linhas da semana anterior no início de toda reunião. Sem essa checagem, em um
mês as pessoas aprendem que nada decorre do bloco, e ele se enche de verbos
vagos.

**O slide vira relatório de status.** Se a reunião é gasta narrando
ATIVIDADES, o formato falhou. Os slides saem 24 horas antes; a reunião é para
obstáculos e decisões.

**Só o líder tem a visão de integração.** O planejamento 1:1 isola o mapa de
dependências — e a E2 depende dos dados da E1, a E4 dos modelos da E2. A
sessão em grupo na abertura existe para expor isso antes de qualquer
compromisso.

**Um passo escorrega e desaparece.** Carregue-o adiante com a data original
visível: *"— A. Lorenzoni, 03/09, transferido de 27/08"*. Um deslize é ruído;
a mesma linha carregada por três semanas é o sinal de que a atividade é mais
difícil do que se estimou, ou está travada por algo que ninguém nomeou.
