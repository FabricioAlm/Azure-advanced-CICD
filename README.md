# Azure-advanced-CICD
Descritivo do desafio de projeto

#Gitignore#

.idea
app/node_modules
*.DS_Store
*tgz
junit.xml


#gitlab-ci.yml#
stages:
  - test

realizar_testes:
  stage: test
  image: node:20.7.0-alpine3.17
  before_script:
    - cd app/
    - npm install
  script:
    - npm test

#Dockerfile#

FROM node:16-alpine

WORKDIR /usr/src/app

COPY ./app/package*.json ./
RUN npm install
COPY ./app .

EXPOSE 3000
CMD ["npm", "start"]
