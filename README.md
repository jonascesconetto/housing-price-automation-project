## Automação de Projetos de Data Science utilizando Apache Airflow
  Este repositório contém alguns arquivos e códigos utilizados durante curso de `Data Pipelines com Apache Airflow `.
### Objetivo do projeto
  - Predição do log do erro entre a estimativa da Zillow e o preço atual dos imóveis.
  - [Link](https://www.kaggle.com/competitions/zillow-prize-1/data) da competição Zillow

Projeto consiste em desenvolver todo o processo de automatização para um projeto de `Data Science`, no qual possui as seguintes etapas:
  1. Carga de dados
  2. Limpeza
  3. Análise e exploraçào
  4. Pré-processamento e transformaçào
  5. Feature Engineering
  6. Ajustes e Avaliação
  7. Deploy
## 💻 Principais Tecnologias, Softwares e Bibliotecas
- Python
- Projeto Anaconda
- Docker 
- Apache AirFlow (Data Pipeline)
## ⚙ Instalação e configuração de ambiente (local)
### Projeto Anaconda
 - Seguir a [documentação](https://www.anaconda.com/) oficial.
## ⚙ Instalação e configuração de ambiente (Docker)
### Docker
  - Seguir a [documentação](https://docs.docker.com/engine/install/) oficial.
### Container - Apache AirFlow
  - `Observação: `Abra o terminal em um diretório raiz para subir seu container com Airflow, dessa forma não perdemos os arquivos de DAGs gerados caso seja necessário algumas reinstalação ou configuração adicional do container.
  - Crie container com seguinte comando em seu terminal:
    ```bash
    docker run -d -p 8080:8080 -v "$PWD/airflow/dags:/opt/airflow/dags/" \
    --entrypoint=/bin/bash \
    --name airflow apache/airflow:2.3.4-python3.8 \
    -c '(\
    airflow db init && \
    airflow users create --username <nome de usuário> --password <sua senha> --firstname <Seu nome> --lastname <Seu Nome> --role Admin --email <Seu e-mail>); \
    airflow webserver & \
    airflow scheduler\
    '
    ```
  - Verificando o container em execução.
    ```bash
    docker container ls
    ```
  - Verificando os logs do container
    ```bash
    docker container logs airflow
    ```
  - Se nenhum erro aparecer, acesse a interface web do Apache Airflow pelo endereço:
    
    **https://localhost:8080**
### Instalando bibliotecas necessárias
  - Acessar o container do Airflow como root
    ```bash
    docker container exec -it --user root airflow bash
    ```
  - Seaborn joblib
    ```bash
    pip install joblib
    ```
  - Sklearn
    ```bash
    sudo pip install sklearn
    ```
## Executando 
### Testar o `notebook`do projeto
  - Dentro do diretório `notebooks` executar cada um dos arquivos listados.
### Testar a `DAG` do projeto
- `pipeline_data_science_housing_price`  
## Vantagens e Desvantagens 
### Vantagens
- Integração com outros componentes
- Tolerância a falhas
- Alertas personalizados
- Operações independentes
  - Redução do tempo de processamento e custos
- Melhor versionamento e log
- Fácil manutençào e controle de erros
- Melhor controle de fluxos
- Fácil integração entre equipes de Engenharia e Ciência de Dados
### Desvantagens
- Maior curva de aprendizado
- Maior tempo de desenvolvimento