# Assistente Lógico Pessoal

> Atividade da disciplina Linguagem de Programação e Paradigmas · UNIDAVI · 2026/2

**Aluno(a):** Ana Paula Fertig Bastos
**Linguagem do sistema:** Python

## O que é

Uma base de conhecimento em Prolog (`meus_dados.pl`) com fatos e regras sobre mim e um assistente em linha de comando que consulta essa base pela ponte (`prolog.py` ou `prolog.js`).

## Como executar

Requisitos: SWI-Prolog no PATH e Python 3 **ou** Node.js.

```bash
# testar a ponte
python teste_ponte.py      # ou: node teste_ponte.js

# executar o assistente
python assistente.py       # ou: node assistente.js
```

## Minha base

- Fatos: `eu/1`, `cursa/3`, `compromisso/3`, `sabe/2`, `gosta/2`
- Regras: `ocupado/2`, `livre/2`, `o_que_faco/3`, `pode_ensinar/1`, `dia_cheio/1` e a minha regra abaixo
`devo_estudar/2`

## Minha regra (R6) - Devo estudar se estou livre

```prolog
% R6 · Devo estudar se estou livre e o dia não está cheio
devo_estudar(Dia, Turno) :- livre(Dia, Turno), \+ dia_cheio(Dia).
```

**O que ela significa:** A regra 6 implementada verifica se o dia está livre no dia e/ou turnos inseridos. O livre(Dia, Turno) verifica se o dia e turnos estão livres, isso é, se não existe compromisso naquele dia e se o dia não estiver cheio. O objetivo é, a partir dessa verificação, identificar qual dia está livre para estudo, a fim de verificar qual dia é possível estudar.
1. Verificar a disponibilidade: identificar se o turno informado está livre, por meio do predicado livre(Dia, Turno), verificando a inexistência de compromissos no período.
2. Verificar a ocupação do dia: identificar se o dia não está completamente ocupado, utilizando a negação do predicado dia_cheio(Dia).

## Saída real do assistente

```text
Resultado Opção 1: 
== Minhas disciplinas ==
  - lpp (quarta, noite)
  - rede_de_computadores (segunda, noite)
  - desenvolvimento_plataformas_moveis (terca, noite)
  - gerencia_de_projetos (quinta, noite)
  - seguranca_em_alimentos (sexta, noite)


Resultado Opção 6:
Categoria (serie, comida, hobby, musica...): serie

== Gosto de (serie) ==
  - modern family
  - the office
  - breaking bad


Resultado Opção 8 (minha regra):
== Dias e turnos em que devo estudar ==
  - terca de manha
  - terca de tarde
  - quinta de manha
  - quinta de tarde
  - sexta de manha
  - sexta de tarde
  - sabado de manha
  - sabado de tarde
  - sabado de noite
```
