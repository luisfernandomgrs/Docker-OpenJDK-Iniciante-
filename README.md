# Docker-OpenJDK-Iniciante-
Ainda como iniciante, Estou sempre procurando um material de estudo e hoje foi a vez do Java

<h1>Criando um Ambiente Docker usando OpenJDK</h1>

Olá, pessoal
hoje resolvi compartilhar aqui o que estou aprendendo no meu dia-a-dia... vamos la´.

Depois que brinquei bastante com docker criando ambientes de desenvolvimento para php+mysql+nginx seguindo um vídeo da DigitalOcean com a @ErikaHeidi que gosto muito, :)
resolvi ver como seria usando WSL2 + Docker + Java + OpenJDK, com Visual Studio Code ;)

Pa variar não gosto de ficar instalando um monte de coisas no meu computador, daí ter gostado tanto de docker que mesmo sendo um pouco difícil para iniciantes, estou gostando muito.

Vamos lá então.
---------------

Neste link  está o vídeo de exemplo que escolhi para treinar hoje: https://youtube.com/watch?v=mean7OgfF44
O detalhe é que apesar do exemplo ser apenas um HelloWorld em java, o que realmente importa é o uso do docker e o aprendizado no uso do arquivo dockerfile, ok.

No vídeo o que vemos é um exemplo de HelloWord... que logo mais abaixo, veremos.

Neste ponto ao invés de copiar o conteúdo do dockerfile conforme o vídeo, optei por usar o exemplo diretamente do DockerHub para o OpenJDK, conforme o link: https://hub.docker.com/_/openjdk

<h2>De forma simples, digite o código abaixo e salve com o nome "HelloWord.java", sem as aspas:</h2>

Gosto do VSCode como editor, mas use o de sua preferência
<pre>
    <code>
        public class HelloWorld {
            public static void main(String[] args)
            {
                System.out.println("Hello World");
            }
        }
    </code>
</pre>

<h4>No mesmo local de sua aplicação de exemplo, crie um arquivo com o nome "dockerfile" sem nenhuma extensão, com o seguinte conteúdo:</h4>
<pre>
  <code>
    FROM openjdk:7
    COPY . /usr/src/myapp
    WORKDIR /usr/src/myapp
    RUN javac http://HelloWord.java
    CMD ["java", "Main"]
  </code>
</pre>

Você consegue executar e fazer o build da imagem, com os seguintes comandos:
<pre>
  <code>
docker build -t my-java-app .
$ docker run -it --rm --name my-running-app my-java-app
  </code>
</pre>
O que gosto no Docker é isso, não precisar fazer configurações que ficarão acumuladas em meu equipamento mesmo quando não estiver usando! Isso é incrível :)

No fim da execução da aplicação, a imagem continuará existindo conforme podemos ver pelo comando:
<pre>
    <code>
        docker images
    </code>
</pre>
Se desejar remover todos os objetos do docker que não estão mais em uso, execute o comando:
<pre>
    <code>
        docker system prune
    </code>
</pre>
Espero ter ajudado, :)
