# Sistema de Gestão de Transportes

## Descrição Geral
A empresa **TransLogística S.A.** opera no segmento de transporte rodoviário de cargas e precisa de um sistema para gerenciar suas operações logísticas.  
O sistema deve controlar **rotas, motoristas, veículos, cargas e entregas**, permitindo o acompanhamento em tempo real, otimização de processos e geração de relatórios gerenciais.

---

## Requisitos Funcionais
- Cadastro de **motoristas**, **veículos** e **clientes**.
- Planejamento e registro de **rotas** e **viagens**.
- Controle de **cargas** transportadas, incluindo origem, destino, tipo e peso.
- Acompanhamento do status das **entregas** (planejada, em trânsito, entregue, atrasada).
- Emissão de documentos de transporte (CT-e, manifesto de carga).
- Registro de **manutenção de veículos** e controle de custos operacionais.
- Rastreamento de veículos e cargas em tempo real.
- Geração de relatórios de desempenho (entregas, custos, utilização de frota).
- Auditoria de ações críticas (cadastro, alteração, exclusão de dados).

---

## Regras de Negócio Detalhadas

### 1. Cadastro e Vinculação
- Cada **motorista** pode ser vinculado a um ou mais **veículos**.
- Cada **viagem** é associada a uma **rota** previamente cadastrada, contendo pontos de origem e destino.
- O cadastro de **cargas** deve conter informações detalhadas: tipo, peso, volume, valor, cliente remetente e destinatário.
- Um veículo só pode ser alocado a uma viagem se estiver com manutenção em dia e documentação válida.

### 2. Planejamento e Execução de Viagens
- O planejamento de uma viagem exige a seleção de rota, veículo, motorista e carga.
- O sistema deve calcular automaticamente o tempo estimado de viagem e custos previstos (combustível, pedágios, diárias).
- Viagens só podem ser iniciadas após aprovação do gestor logístico.
- O status da entrega deve ser atualizado em tempo real: Em trânsito, Entregue, Atrasada, Cancelada.

### 3. Controle de Entregas e Auditoria
- Cada entrega deve ser registrada com data/hora de saída, chegada e confirmação do destinatário.
- Em caso de atraso, o sistema deve notificar automaticamente o gestor e o cliente.
- Todas as ações de cadastro, alteração ou exclusão de viagens, cargas e entregas devem ser registradas em log de auditoria, com identificação do usuário responsável.

### 4. Manutenção e Custos Operacionais
- O sistema deve controlar datas de manutenção preventiva e corretiva dos veículos.
- Veículos com manutenção pendente não podem ser alocados a novas viagens.
- Custos operacionais (combustível, pedágios, manutenção, diárias) devem ser registrados e vinculados à viagem correspondente.

### 5. Relatórios e Indicadores
- O sistema deve gerar relatórios de desempenho por período, motorista, veículo, rota e cliente.
- Indicadores obrigatórios: entregas realizadas, atrasos, custos por viagem, utilização da frota, rentabilidade por cliente.

---

## Observações Técnicas para a Modelagem

- Modelar os dados até a **4ª Forma Normal**, eliminando redundâncias e dependências multivaloradas.
- Desnormalizar apenas para facilitar consultas frequentes (ex: incluir nome do cliente na tabela de entregas).
- Todas as tabelas, quando necessário, devem conter atributos de manutenção:
  - `UsuarioCriacao` (VARCHAR)
  - `DataCriacao` (DATETIME)
  - `UsuarioUltimaAtualizacao` (VARCHAR)
  - `DataUltimaAtualizacao` (DATETIME)
- Tipagem sugerida:
  - Chaves primárias: `INT` autoincrement.
  - Campos textuais: `VARCHAR` com tamanho apropriado.
  - Valores numéricos: `DECIMAL` para peso, custo, valor de carga.
- Separar schemas com cores diferentes conforme cada área do sistema:
  - `Operacional` (Viagens, Rotas, Entregas, Cargas, Veículos, Motoristas)
  - `Administrativo` (Clientes, Usuários)
  - `Financeiro` (Custos)

## Branchs

- Clone o repositorio
- Crie sua branch com git checkout -b feat/seuNomeAqui
- Na sua branch configure o upstream: git push -u origin feat/SuaBranch
- Faça tudo apenas NA SUA BRANCH
- Subir sua modelagem em png
---
