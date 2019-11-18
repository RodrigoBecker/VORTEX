# vortex - Show me the Code 
Project-Vortex

** Dependencias ** 

# DOCKER 
# DOCKER COMPOSE 


**Estrutura do arquivmo application.yaml** 


      version: '3.4'
      services: 

         app_metabase:
            image: metabase/metabase
            container_name: matabase_app
            hostname: app-metabase
            ports:
              - "8080:8080"
            depends_on:
              - database

         database: 
           image: mysql
           container_name: database
           environment:
           - MYSQL_USER=root
           - MYSQL_ALLOW_EMPTY_PASSWORD=yes
           - MYSQL_DATABASE=app_metabase
      


**Comandos para orquestração dos Containers** 

            docker ps -a listar os containers 
            docker rm -f | remover containers 
            docker image list lista Imagens 
            docker rmi Remover Imagens 


**Utilização de plataforma**

Poderiamos utilizar tais plataformas para utilização deste cenário, para montar o pipeline: 

 * HEROKU 
 * AMAZON ELASTIC BENS STALCK 
 * AZURE 
 * JENKINS 
 * TRAVIS CI


 **Cenário de CI|CD *

Poderiamos instalar a ferramenta jenkins em um container juntamente o repositório GITLAB, pois por ser openSource, conseguimos subir uma aplicação de um repositorio git localmente em nosso servidor, assim poderiamos configurar o Jenkins utilizando através de seus plugins, para que possamos montar o pipeline de "deployment" se conectandp com o repositório e configurar as triggers para o deploy da aplicação com base nos pull request e merge request. 

**Exemplo do Trecho do arquivo applicantion.yaml  com as configurações de inicialização dos containers** 

         jenkins: 
           image: jenkins
           container_name: jenkins
           hostname: serve-jenkins
           ports:
              - "8080:8080"
              - "50000:50000"


         gitlab: 
            image: gitlab/gitlab-ce
            container_name: gitlab
            hostname: gitlab
            ports:
             - "80:80"
             - "443:443"
             - "22:22"


