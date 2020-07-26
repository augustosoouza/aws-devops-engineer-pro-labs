# Lab 02 - CodeBuild
Realizando testes da aplicação usando AWS CodeBuild

# 1. Criando Build Projecy

1.1 Em CodeBuild (https://sa-east-1.console.aws.amazon.com/codesuite/codebuild/start?region=sa-east-1), clicar em create Project. 

![Image 01](./img/lab1.1.png)

1.2 Primeiro vamos dar um nome para nosso projeto e escolher qual o source provider da nossa aplicação. Neste caso é o CodeCommit (MyFirstRepo), mas o CodeBuild aceita como source: BitBucket, GitHub, S3 e GitHub Enterprise.
Tambem será perguntado qual a referencia para o build. Neste lab vamos escolher Branch - Master, mas poderiamos escolher uma TAG no caso de testar uma versão especifica do codigo ou um commitID especifico.

![Image 02](./img/lab1.2.png)

1.3 Agora, devemos escolher o ambiente para o build. A imagem poderá ser uma imagem padrão da AWS ou podemos usar uma imagem docker customizada, para laboratorio, vamos usar a imagem default amazon Linux. Vamos usar tambem o Runtime e imagem mais recente.
Para executar o CodeBuild, é necessario uma role IAM especifica, o CodeBuild poderá criar para voce caso não tenha uma, basta nomea-la.
*Não vamos mexer com configurações adicionais no momento.

![Image 03](./img/lab1.3.png)

1.4 Em Buildspec, é onde definimos as fases de teste do codigo. Neste caso eu já criei um builspec e subi para nosso repositorio. Mas o CodeBuild permite voce inserir os comando manualmente disponibilizando um editor.
Artifacts não iremos usar nesse lab. O CodeBuild permite armazenar o artefato no S3. Logs vamos manter no CloudWatch padrão, mas tambem é possivel usar o S3 para facilitar o debug. 
Finalizado, clicamos em Create Build Project.

![Image 04](./img/lab1.4.png)

1.5 Projeto criado, agora vamos clicar em "Start Build".

![Image 05](./img/lab1.5.png)

Novamente irá aparecer as configurações do build. As unicas opções disponiveis para serem alteradas são a Referencia e adicionar uma variavel. Não vamos alterar nada e clicar em "start build"

![Image 06](./img/lab1.6.png)

1.6 Nosso container para build foi inializado, com isso conseguimos acompanhar o log, as fases do build, etc. 

![Image 07](./img/lab1.7.png)

![Image 08](./img/lab1.8.png)

Tambem é possivel visualizar o log completo no cloudwatch, clicando em "view intire log". Assim facilitar o debug.

![Image 09](./img/lab1.9.png)

Todos os builds ficarão disponiveis em Build History com as informações do build. 

![Image 10](./img/lab1.10.png)



documentação referencia:

https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html

https://docs.aws.amazon.com/codebuild/latest/userguide/samples.html