# FIAP - Faculdade de Informática e Administração Paulista

<p align="center">
<a href="https://www.fiap.com.br/"><img src="assets/logo-fiap.png" alt="FIAP - Faculdade de Informática e Administração Paulista" border="0" width=40% height=40%></a>
</p>

<br>

# Gestão Agrícola com Sensoriamento - FarmTech Solutions

## FarmTech Group

## 👨‍🎓 Integrantes:
- <a href="https://www.linkedin.com/in/seu-perfil">Seu Nome Completo</a>
- <a href="https://www.linkedin.com/in/integrante2">Nome do Integrante 2</a>
- <a href="https://www.linkedin.com/in/integrante3">Nome do Integrante 3</a>
- <a href="https://www.linkedin.com/in/integrante4">Nome do Integrante 4</a>
- <a href="https://www.linkedin.com/in/integrante5">Nome do Integrante 5</a>

## 👩‍🏫 Professores:
### Tutor(a)
- <a href="https://www.linkedin.com/in/tutor">Nome do Tutor</a>
### Coordenador(a)
- <a href="https://www.linkedin.com/in/coordenador">Nome do Coordenador</a>

## 📜 Descrição

Este projeto, desenvolvido pela equipe **FarmTech Solutions**, visa criar um sistema de banco de dados relacional para gestão agrícola com foco em agricultura digital. O objetivo é armazenar e analisar dados coletados por sensores instalados em campos agrícolas, monitorando condições como umidade (sensor S1), pH (sensor S2) e níveis de nutrientes como fósforo (P) e potássio (K) (sensor S3). Esses dados são usados para sugerir ajustes otimizados de irrigação e aplicação de nutrientes, aumentando a produtividade e a sustentabilidade.

O sistema suporta o registro de campos, plantios, culturas, leituras de sensores e ajustes realizados. Ele permite consultas analíticas, como a quantidade total de água aplicada por mês ou a variação de pH ao longo do tempo, auxiliando agricultores a tomar decisões baseadas em dados. O modelo foi projetado com relacionamentos 1:N para refletir a realidade operacional, onde, por exemplo, um campo pode ter vários sensores e um plantio pode receber múltiplos ajustes.

## 📁 Estrutura de pastas

Dentre os arquivos e pastas presentes na raiz do projeto, definem-se:

- **.github**: Arquivos de configuração específicos do GitHub para gerenciar o repositório.
- **assets**: Imagens e elementos visuais, como o diagrama DER.
- **config**: Arquivos de configuração do projeto.
- **document**: Documentação do projeto, incluindo o modelo de dados.
  - **other**: Documentos complementares.
- **scripts**: Scripts auxiliares (ex.: geração de relatórios).
- **src**: Código-fonte desenvolvido ao longo do projeto.
- **README.md**: Guia geral do projeto.

## 🔧 Como executar o código

### Pré-requisitos
- **Oracle SQL Developer Data Modeler**: Versão mais recente (disponível em <https://www.oracle.com/br/database/sqldeveloper/technologies/sql-data-modeler/download/>).

### Instalação e Execução
1. Baixe o repositório do GitHub.
2. Abra o arquivo `FarmTech_Model.dmd` no Oracle SQL Developer Data Modeler.
3. Visualize o diagrama lógico no painel **"Logical Model"**.
4. Para gerar o esquema físico, clique em **"Tools" > "Engineer to Relational Model"**.

## 🗃 Histórico de lançamentos

- **0.2.0 - 25/10/2024**
  - Adição de atributos faltantes às entidades e exportação do DER atualizado.
- **0.1.0 - 15/10/2024**
  - Criação do modelo inicial com entidades e relacionamentos.

## 📋 Licença

<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1"><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1"><p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/agodoi/template">MODELO GIT FIAP</a> por <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://fiap.com.br">Fiap</a> está licenciado sobre <a href="http://creativecommons.org/licenses/by/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">Attribution 4.0 International</a>.</p>

---

## Modelo Entidade-Relacionamento (MER)

### Entidades e Atributos
- **Campo**
  - **ID_Campo** (PK, INT): Identificador único do campo.
  - **Descricao** (VARCHAR(100)): Descrição do campo.
  - **Area** (DOUBLE): Área do campo em hectares.

- **Sensor**
  - **ID_Sensor** (PK, INT): Identificador único do sensor.
  - **ID_Campo** (FK, INT): Referência ao campo.
  - **Tipo_Sensor** (VARCHAR(10)): Tipo do sensor ('S1', 'S2', 'S3').
  - **Localizacao** (VARCHAR(100)): Localização no campo.

- **Leitura_Sensor**
  - **ID_Leitura** (PK, INT): Identificador único da leitura.
  - **ID_Sensor** (FK, INT): Referência ao sensor.
  - **Data_Hora** (DATETIME): Data e hora da leitura.
  - **Tipo_Valor** (VARCHAR(10)): Tipo de valor medido ('umidade', 'pH', 'P', 'K').
  - **Valor** (DOUBLE): Valor numérico da leitura.

- **Cultura**
  - **ID_Cultura** (PK, INT): Identificador único da cultura.
  - **Nome_Cultura** (VARCHAR(50)): Nome da cultura (ex.: "Milho").

- **Plantio**
  - **ID_Plantio** (PK, INT): Identificador único do plantio.
  - **ID_Campo** (FK, INT): Referência ao campo.
  - **ID_Cultura** (FK, INT): Referência à cultura.
  - **Data_Inicio** (DATE): Data de início do plantio.
  - **Data_Fim** (DATE): Data de fim do plantio (NULL se ativo).

- **Ajuste_Irrigacao**
  - **ID_Ajuste_Irrigacao** (PK, INT): Identificador único do ajuste.
  - **ID_Plantio** (FK, INT): Referência ao plantio.
  - **Data_Hora** (DATETIME): Data e hora do ajuste.
  - **Quantidade_Agua** (DOUBLE): Quantidade de água aplicada (litros).

- **Ajuste_Nutrientes**
  - **ID_Ajuste_Nutrientes** (PK, INT): Identificador único do ajuste.
  - **ID_Plantio** (FK, INT): Referência ao plantio.
  - **Data_Hora** (DATETIME): Data e hora do ajuste.
  - **Tipo_Nutriente** (VARCHAR(10)): Tipo de nutriente ('P', 'K').
  - **Quantidade_Nutriente** (DOUBLE): Quantidade aplicada (kg).

### Relacionamentos
- **Campo 1:N Sensor**: Um campo pode ter vários sensores.
- **Sensor 1:N Leitura_Sensor**: Um sensor pode gerar várias leituras.
- **Campo 1:N Plantio**: Um campo pode ter vários plantios.
- **Cultura 1:N Plantio**: Uma cultura pode ser plantada em vários plantios.
- **Plantio 1:N Ajuste_Irrigacao**: Um plantio pode ter vários ajustes de irrigação.
- **Plantio 1:N Ajuste_Nutrientes**: Um plantio pode ter vários ajustes de nutrientes.

### Lógica de Negócio
Os sensores monitoram condições do solo em tempo real, gerando leituras que alimentam o sistema. Com base nessas leituras, ajustes de irrigação e nutrientes são registrados por plantio, otimizando o uso de recursos e a produtividade agrícola.