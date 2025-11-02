# Modelos de Dados

## Entidade: Usuário  
| Atributo        | Tipo         | Comentário                          |
|-----------------|--------------|------------------------------------|
| id              | UUID         | identificador único                |
| email           | VARCHAR(255) | único, indexado                    |
| senha_hash      | VARCHAR(255) | hash da senha                      |
| criado_em       | TIMESTAMP    | data de registro                   |

## Entidade: Projeto  
| Atributo        | Tipo         | Comentário                          |
|-----------------|--------------|------------------------------------|
| id              | UUID         |                                      |
| nome            | VARCHAR(255) |                                      |
| dono_id         | UUID (FK)    | usuário que criou o projeto         |
| criado_em       | TIMESTAMP    |                                      |

## Entidade: Tarefa  
| Atributo        | Tipo         | Comentário                          |
|-----------------|--------------|------------------------------------|
| id              | UUID         |                                      |
| projeto_id      | UUID (FK)    | referência ao projeto               |
| titulo          | VARCHAR(255) |                                      |
| descricao       | TEXT         |                                      |
| autor_id        | UUID (FK)    | usuário que criou                   |
| responsavel_id  | UUID (FK)    | usuário que está responsável       |
| data_vencimento | DATE         |                                      |
| estado          | ENUM         | {TO_DO, IN_PROGRESS, DONE}          |
| criado_em       | TIMESTAMP    |                                      |
| atualizado_em   | TIMESTAMP    |                                      |

## Relacionamentos  
- Um *Projeto* pertence a um único *Usuário* (dono).  
- Um *Projeto* tem vários *Usuários* (membros) — relação muitos‑para‑muitos (tabela Projeto_Usuario).  
- Uma *Tarefa* pertence a um *Projeto*.  
- Uma *Tarefa* tem autor e responsável, ambos são *Usuário*.  

## Índices recomendados  
- Usuário: índice único sobre email  
- Tarefa: índice composto sobre (projeto_id, responsavel_id, estado) para consulta de painel  

